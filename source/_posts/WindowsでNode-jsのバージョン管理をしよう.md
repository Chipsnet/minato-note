---
title: WindowsでNode.jsのバージョン管理をしよう
date: 2020-04-15 20:36:24
tags: ["Node.js"]
categories: ["技術"]
---
# 前提

- Chocolaty導入済み
- Node.js導入済み
- Windows10

# 選択肢

WindowsのNode.jsバージョン管理ツールには２種類ある

- nodist
- nvm-windows

nvm-windowsとnodist、どちらも人気があるように思える
とりあえず今回は頻繁にメンテナンスされている（ように見える）nvm-windowsを使う

# Node.jsのアンインストール

Node.jsがあるとnvm的に問題がある（nvm側に切り替わらない）らしく、まずはNode.jsをアンインストールしておく。

これは各自やってください。

# インストール

`choco install nvm -y`

これで勝手にインストールされます。
やったぜ

# バージョン切り替え

`nvm list available` で、インストールできるNodeバージョン（一部）がリストで出ます。

`nvm install [version]` で指定したバージョンのNode.js（とnpm）がインストールされます。

`nvm list` で、インストール済みのNode.js一覧が見れます。

`nvm use [version]` で、インストールしたNode.jsに切り替わります。

> nvm use を実行しないと切り替わらないので注意

# おわり

めちゃ簡単でしたね。これでいろいろ楽になりそうです。