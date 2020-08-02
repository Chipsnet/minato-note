---
title: Goで独自パッケージがimportできない
date: 2020-07-28 20:05:11
tags:
    - Golang
    - VisualStudioCode
categories: 技術
---
現在、以下の構成

```
warbot-go
├ test
│ └ test.go
├ go.mod
└ hello.go
```

この状態で`hello.go`から`test.go`をimportできない。
まず、保存しようとするとコードが消える

これはVSCodeに入れているGolintが消してるっぽい
ログには
`Not able to determine import path of current package by using cwd: c:\Users\Minato86\repos\MyRepository\warbot-go and Go workspace: `
と記録されていた。

まずは今の状況を振り返っておくと
- `go mod init warbot-go`でmodを初期化済み
- `go env`の`GO111MODULE`はonになっている

というわけで、今はGo Modulesが使える環境が整っているはずです。

`main.go`と`test.go`は以下のようになっています

main.go
```go
package main

import (
	"fmt"
	//ここに"warbot-go/test"をimportしたい
)

func main() {
	fmt.Println("Hello, world.")
}

```

test.go
```go
package test

import (
	"fmt"
)

func Test() {
	fmt.Println("test module ready.")
}
```

# linterを無効にしてみる

![2fd55a2ce3bace7661665a70d5dd51c9.png](https://i.gyazo.com/2fd55a2ce3bace7661665a70d5dd51c9.png)

VSCodeのワークスペース設定から、Lint On Saveをoffにしてみる。

結論からいうと、offにしたのに普通に実行された。
なんでや。と思ったら、どうやらこの動作はlinterの仕業ではなく、formatterの仕業みたい。

# formatterを変えてみる

![b373f1c941646a7873dc5913665eb082.png](https://i.gyazo.com/b373f1c941646a7873dc5913665eb082.png)

デフォルトのgoreturnsではなく、gofmtに変えてみた。
結論から言えば、うまくいった。

```go
package main

import (
	"fmt"
	"warbot-go/test"
)

func main() {
	test.Test()
	fmt.Println("Hello, world.")
}
```

消されずにこのように書くことができた。
また、普通に実行できた。

# そういえば

Githubでリポジトリを公開する場合、こっちのほうが正しいっぽい

`go mod init github.com/chipsnet/warbot-go`

あとはimportも`github.com/chipsnet/warbot-go/test`に書き換える。

↓GoなんもわからんからDiscordBotを作っている
[GitHub - Chipsnet/warbot-go: WARbot written in golang](https://github.com/Chipsnet/warbot-go)