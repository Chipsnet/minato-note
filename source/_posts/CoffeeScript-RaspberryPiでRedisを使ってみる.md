---
title: CoffeeScript + RaspberryPiでRedisを使ってみる
date: 2020-03-13 14:17:15
tags: ["CoffeeScript", "RaspberryPi", "Redis"]
categories: ["技術", "データベース"]
---

mongoDB入れようと思ったらラズパイでインストールできるバージョン古すぎて使えなかったので
CoffeeScriptからRedisを使う覚書

# 環境

- Server
  - Raspberry Pi Zero（Raspberry Pi 3に置き換え予定）
  - OS: Raspbian（debian系）
- Client
  - G-GEAR（ゲーミングノート）
  - OS: Windows10 Home
- CoffeeScript
  - v2.5.1
- Node.js
  - v12.13.1
- Yarn
  - v1.21.1

# 前提

- CoffeeScript導入済み
- Node.js導入済み
- Yarn(or npm)導入済み
- Raspberry PiとはSSH通信可能

# Redisのインストール

## インストール

まずは`sudo apt update`でアップデート

その後に`sudo apt install redis-server`でRedisをインストールします。

`ps aux | grep redis`でredisが動いているのを確認できます。

`redis-cli`で対話的に操作することもできます。
`quit`で終了できます。

## 外部からの接続を許可

`sudo nano /etc/redis/redis.conf`でコンフィグファイルを開いて編集します。

```
- bind 127.0.0.1 ::1
+ # bind 127.0.0.1 ::1
```

また、パスワードも設定します。

```
- # requirepass ...
+ requirepass ...
```

`sudo service redis-server restart`で再起動します。

# 接続する

まずは接続のためにCoffeeScriptを書きます。
接続にはredisパッケージを使います。

`yarn add redis`でインストールします。

そして、`redis.coffee`（名前なんてどうでもいいですけど）を作って認証情報諸々書きます

```coffeescript
redis = require 'redis'

config =
    host: '192.168.x.x',
    port: '6379',
    password: 'xxxx'

client = redis.createClient config

client.on 'ready', (err) ->
    console.log 'connected.'

```

hostにはラズパイのローカルIPアドレスを入れます。
passwordにはさっきファイルに書き込んだパスワードを入れます。

正常に接続できれば`connected.`と表示されるはずです。

# おわり

結構簡単でびっくりしました。
まだセキュリティのかけらもないので、諸々やっていきたいと思います。

CoffeeScript書きやすいわ。いいね。