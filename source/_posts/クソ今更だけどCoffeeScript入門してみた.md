---
title: クソ今更だけどCoffeeScript入門してみた
date: 2020-03-13 05:49:11
tags: ["CoffeeScript"]
categories: ["技術"]
---

コミュニティ死んでてマジで終わりそうなCoffeeScriptを書きます。
覚書がてら環境構築をしていく。

# なぜ今更？

- Pythonっぽかったから
- JavaScript書くの飽きたから
- 単純に面白そうだったから

やっていこう

# 前提

- Node.jsがインストールされている
  - 今回のバージョンは`v12.13.1`
- npmがインストールされている
  - 今回のバージョンは`v6.12.1`

# CoffeeScriptのインストール

WindowsならコマンドプロンプトとかPowershell、その他ならTerminalで以下のコマンドを実行するだけ

`npm install --global coffeescript`

一発で入ってしまう。

ちなみにそのプロジェクトだけで使いたい場合は`--global`を`--save-dev`に読み替えてください。

`coffee -v`と打ってバージョン情報が出たらOK

出なかったらシェルを再起動してください。

# やってみる

```coffeescript
hello = "hello"

console.log hello
```

これでhelloができる（変数作る必要なかったろというツッコミはなしで）

これを`index.coffee`で保存、`coffee index.coffee`で実行できます。

# やってみる②

APIにリクエストして結果を得るやつやってみます。

```coffeescript
cat_api = 'https://aws.random.cat/meow'

request.get {
    uri: cat_api,
    headers: {'Content-type': 'application/json'},
    json: true
}, (err, req, data) ->
    console.log data.file
```

明らかに書きやすい。

# やってみる③

DiscordBot作成に使ってみた。

## コマンドリストにprefixつけるやつ

```coffeescript
command_list = ['cat', 'help']

command_list_withprefix = []
for i in command_list
    command_list_withprefix.push prefix+i
```

Pythonみたいですごく書きやすい

// 追記 2020-03-13

```coffeescript
command_list_withprefix = command_list.map (element) -> prefix+element
```

こっちのほうが賢そう

## Botは弾くやつ

```coffeescript
if message.author.bot and message.author is not client.user
    return
```

これもPythonみたいな書き方ができるので、コードがとても読みやすい

（カッコとかカギカッコだらけだとやっぱり読みづらい）

## 開発モードをコマンドライン引数から判断する

```coffeescript
devmode = if process.argv[2]? and process.argv[2] is 'true' then true else false
```

nullとかundefinedを?って書くだけで判断してくれる神仕様

## 開発モードと通常モードでトークンを分ける

```coffeescript
token_dev = 'dev token here'
token_default = 'default token here'

token = if devmode then token_dev else token_default
```

こんな簡単に書けちゃうのか・・・・
最高すぎ

# 感想

ここまで使いやすい言語とは思わなかったです。
めちゃ使いやすかったので（正直今後の保証はないけど）これからはCoffeeScriptで書いてみようと思います。

また何かCoffeeScriptに関する知見があればここに書いていきます。