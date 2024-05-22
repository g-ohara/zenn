---
title: "Neovim with TexLab in Docker"
emoji: "⚙️"
type: "tech"
topics: ["tex", "neovim", "docker", "texlab", "lsp"]
published: true
---

# 概要
- Docker コンテナ内に [TexLab](https://github.com/latex-lsp/texlab) をインストール
- ホスト環境の Neovim からコンテナ内の TexLab にアクセス

# 手順
1. TexLab + [TeX Live](https://tug.org/texlive/) を含めた Docker イメージを作成
1. Neovim でコンテナ内にアクセスするための設定を追加
1. コンテナを起動し，Neovim で TexLab の機能にアクセスできることを確認

## 1. TexLab + TeX Live を含めた Docker イメージを作成
`Dockerfile` を Git レポジトリの最上位ディレクトリに保存してください．
https://github.com/g-ohara/dockerfiles/blob/036b64c0f781d558a18b1815fbe0151cc01a0fdd/texlab/Dockerfile
イメージを軽量化するために，マルチステージビルドを使用しています．

## 2. Neovim でコンテナ内にアクセスするための設定を追加
以下の2つのコードを ```~/.config/nvim/init.lua``` に追記してください．
https://github.com/g-ohara/dotfiles/blob/b13552d6f0d55c28f24237d5f21b7eab62d7ea4a/.config/nvim/lua/plugins.lua#L47-L59
https://github.com/g-ohara/dotfiles/blob/b13552d6f0d55c28f24237d5f21b7eab62d7ea4a/.config/nvim/lua/plugins.lua#L133-L157

上記コードの ```project_name_to_container_name``` は，カレントディレクトリを含む Git レポジトリの名称 (```.git``` ディレクトリが見つからなければカレントディレクトリの絶対パス) をコンテナ名に変換します．

#### 参考:
https://github.com/neovim/nvim-lspconfig/wiki/Running-language-servers-in-containers

## 3. コンテナを起動し，Neovim で TexLab の機能にアクセスできることを確認
これで準備は完了です．
```compose.yml``` を Git レポジトリの最上位ディレクトリに保存します．
```yaml:compose.yml
services:
  texlab:
    build: .
    container_name: {コンテナ名}
    volumes:
      - ./:${PWD}
    working_dir: ${PWD}
    tty: true
```

`working_dir` を `${PWD}` とし，そこにカレントディレクトリをマウントするのがポイントです．ファイルのパスがホスト側での絶対パスとして Language Server に渡されるので，対象ファイルへのパスを両者の間で一致させておく必要があります．

```docker compose up -d``` を実行したあとに Neovim で TeX ファイルを開くと， TexLab の機能が使用できるはずです．

# まとめ
GitHub で dotfiles や TeX Template を公開していますので，そちらも参考にしてください．
ご質問やご指摘，よりよい設定の紹介などがあれば，ぜひコメントでお知らせください．
https://github.com/g-ohara/dotfiles
https://github.com/g-ohara/tex-template
