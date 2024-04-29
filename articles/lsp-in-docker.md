---
title: "Neovim で Docker コンテナ内の Language Server にアクセスする"
emoji: "⚙️"
type: "tech"
topics: ["neovim", "docker", "lsp", "language server"]
published: true
---

# 概要
### 対象とする読者
- ローカル環境を汚したくない潔癖プログラマ
- Neovim と Docker をこよなく愛するプログラマ

### 願望
- Neovim から Language Server を使って，快適な開発環境を構築したい
- でも，コンパイラやライブラリでローカル環境を穢したくない
- とはいえ， Docker コンテナの中で作業するのはスマートじゃない
- ローカルで動作する Neovim から Docker コンテナ内の Language Server にアクセスして，クリーンで快適な開発環境を構築しよう!

# 手順

1. [neovim/nvim-lspconfig](https://github.com/neovim/nvim-lspconfig) プラグインをインストール
1. ```init.lua``` に設定を追加
1. Git レポジトリで， Language Server がインストールされた Docker コンテナを走らせる

以下では特に，[clangd](https://clangd.llvm.org/) を利用した C/C++ のための開発環境を構築する手順を紹介します．

## 0. ```init.lua``` へ移行
もし ```init.vim``` をお使いでしたら，```init.lua``` へ事前に移行しておくことをお勧めします．Web 上にいくつも解説がありますが，下記のサイトが個人的に分かりやすかったです．
https://minerva.mamansoft.net/Notes/%F0%9F%93%9Cinit.vim%E3%81%8B%E3%82%89init.lua%E3%81%B8%E7%A7%BB%E8%A1%8C%E3%81%99%E3%82%8B
[Vim script](https://ja.wikipedia.org/wiki/Vim_script) の信奉者の皆さまは，これ以降の Lua コードを Vim script に変換して ```init.vim``` に追記してください．

## 1. neovim/nvim-lspconfig プラグインをインストール
https://github.com/neovim/nvim-lspconfig
お使いのプラグインマネージャでインストールしてください．

## 2. ```init.lua``` に設定を追加
以下を ```~/.config/nvim/init.lua``` に追記してください．

```lua:init.lua
local lspconfig = require("lspconfig")

-- https://github.com/neovim/nvim-lspconfig/wiki/Running-servers-in-containers
local root_pattern = lspconfig.util.root_pattern('.git')
local function project_name_to_container_name()
  local bufname = vim.api.nvim_buf_get_name(0)
  local filename = lspconfig.util.path.is_absolute(bufname) and bufname
      or lspconfig.util.path.join(vim.loop.cwd(), bufname)
  local project_dirname = root_pattern(filename) or lspconfig.util.path.dirname(filename)
  return vim.fn.fnamemodify(lspconfig.util.find_git_ancestor(project_dirname), ':t')
end

-- C/C++
lspconfig.clangd.setup {
  cmd = {
    'docker',
    'exec',
    '-i',
    project_name_to_container_name(),
    'clangd',
    '--background-index',
  },
}
```

上記コードの ```project_name_to_container_name``` は，カレントディレクトリを含む Git レポジトリの名称 (```.git``` ディレクトリが見つからなければカレントディレクトリの絶対パス) をコンテナ名に変換します．
```lspconfig.clangd.setup``` は，得られたコンテナ名から ```docker exec -i {コンテナ名} clangd --background-index``` を実行し，以降は当該コンテナ内の Language Server と通信します．
#### 参考:
https://github.com/neovim/nvim-lspconfig/wiki/Running-language-servers-in-containers

## 3. Git レポジトリで， Language Server がインストールされた Docker コンテナを走らせる
これで準備は完了です．
以下の ```hello-world.cc``` と ```docker-compose.yml``` を Git レポジトリの中の同一ディレクトリに保存します．

```cpp:hello-world.cc
#include <iostream>

int main() {
  std::cout << "Hello, World!" << std::endl;
  return 0;
}
```

```yaml:docker-compose.yml
services:
  gcc:
    image: lspcontainers/clangd
    container_name: {レポジトリ名}
    volumes:
      - ./:/usr/src/myapp
    working_dir: /usr/src/myapp
    tty: true
```

```docker compose up -d``` を実行したあとに Neovim で ```hello-world.cc``` を開くと， Builtin LSP の機能が使用できるはずです．もしステータスラインに ```Client 1 quit with exit code 1 and signal 0``` などと表示された場合は，
- Neovim が探しているコンテナ名と実際のコンテナ名が一致していない
- 当該コンテナで ```clangd``` を実行できない

といった原因が考えられます．

# まとめ
Docker コンテナ内の Language Server を用いた開発環境の構築方法について簡単に紹介しました．最小限の設定のみを紹介しましたので，これを実用に堪えるまでに快適にするためには，LSPの詳細な設定が必要です．通常の設定と同様に行えばよいと思いますが，私たちの使用法に特化した設定が必要な場合もあるでしょう．
ご質問やご指摘，よりよい設定の紹介などがあれば，ぜひコメントでお知らせください．
