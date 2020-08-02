---
title: Go言語ことはじめ
date: 2020-07-29 04:23:08
tags:
    - Golang
categories: 技術
---
# 環境

- Windows10
- Chocolatey導入済み

# Go言語の導入

`choco install golang` を実行すると、Go言語をインストールできます。
更新するときは `choco upgrade golang` でできます。

# VSCodeに拡張機能を導入

[![Image from Gyazo](https://i.gyazo.com/da73eb8a0e215e2b77ce03713816199e.png)](https://gyazo.com/da73eb8a0e215e2b77ce03713816199e)

拡張機能検索に`Go`と入力すると、一番上に公式の拡張機能が出てくるのでインストールします。

インストールが終わったら、コマンドパレット（Ctrl+Shift+P）を開き、`Go: Install/Update Tools`を検索して、実行します。

すると、拡張機能の動作に必要なツール一式がダウンロードされます。

これで拡張機能の導入は完了です。

# 書いてみる

`hello.go`を作成します。
内容を以下のように作成します。

```go
package main

import (
	"fmt"
)

func main() {
	fmt.Println("Hello, world.")
}
```

そして保存、`go run hello.go`を実行すると`Hello, world.`が実行されます。

# 解説

## package

感覚的にはJavaやC#などの名前空間に近いですが、厳密には違うものみたいです。

これは、importするときに指定される名前です。

基本的にはディレクトリ名を付けることが推奨されていて、例えば`app`というディレクトリに`main.go`を作ったとすると、最初を`package app`とすることが推奨されているということです。

Go Modulesの仕様上、外部からダウンロードしたパッケージと被っても問題ありません。

そこらへんはここに書いてます [Goで独自パッケージがimportできない - MinatoNote](https://blog.minato86.me/2020/07/28/Go%E3%81%A7%E7%8B%AC%E8%87%AA%E3%83%91%E3%83%83%E3%82%B1%E3%83%BC%E3%82%B8%E3%81%8Cimport%E3%81%A7%E3%81%8D%E3%81%AA%E3%81%84/)

そしてこれが最も重要ですが、ルートディレクトリに配置されているプログラムは`package main`とする必要がります。

そうしないと`go run: cannot run non-main package`というエラーで実行できません。

## import

パッケージをimportします。

今回は、fmtというgolangの入出力を司るパッケージをimportしました。

golangには、github上に無数のパッケージが存在していて、`go get [repos]`というコマンドで簡単にダウンロード、importすることができます。

これによって、開発を高速化することが可能です。

## func main()

`func`と聞けば関数ということはまぁわかると思うんですが、golangでは、main()という関数が一番最初に実行されます。

なので、`func main()`としています。

mainパッケージ内では、かならずmain関数を書かなければなりません。

mainパッケージにmain関数が存在しない場合は `function main is undeclared in the main package` エラーが発生します。

# おわり

以上がGo言語ことはじめです。

正直今回は、Goを使う上での目玉機能には全く触れていません。

- めっっちゃ楽な並列処理
- ビルドして高速実行できる機能

など、Goには素晴らしい機能が何個かあります。
これはもしかしたら続きの記事を作るかもしれないです。