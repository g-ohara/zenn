---
title: "dhclient による IP アドレスの再取得"
emoji: "⚙️"
type: "tech"
topics: ["dhclient", "linux", "network"]
published: true
---

# 概要

Ubuntu 22.04 で有線接続の不具合が発生
- `git clone` や `git submodule update` で重いデータをダウンロードすると有線接続が切れる
- コンピュータの再起動や `systemctl restart NetworkManager` の実行では解決せず
- `dhclient` で IP アドレスを再取得することで解決したのでメモ

# 手順

1. `nmcli` でプロファイル名を確認
   ```sh
   $ nmcli
   eno1: connected to Wired connection 1
           "Intel I219-LM"
           ...
   ```
1. `dhclient` で IP アドレスを破棄・再取得
   ```sh
   # IP アドレスを破棄
   sudo dhclient -v -r eno1
   # IP アドレスを再取得
   sudo dhclient -v eno1
   ```
