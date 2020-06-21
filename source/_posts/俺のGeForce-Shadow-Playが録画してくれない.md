---
title: 俺のGeForce Shadow Playが録画してくれない
tags: ["GeForce", "グラフィックボード", "ドライバ"]
categories: ["不具合"]
date: 2020-05-24 16:31:06
---
[![Image from Gyazo](https://i.gyazo.com/bcc59ecc25348acaa2630b47f158f7b5.png)](https://gyazo.com/bcc59ecc25348acaa2630b47f158f7b5)

こんな表示がでてGeForce Shadow Playの録画ができない。

- 最新のGeForce Game Ready Driverを導入済み
- GeForce Experienceも最新

こんな感じ。

スペック的には

[![Image from Gyazo](https://i.gyazo.com/632295ab455798906a43c34506fa0472.png)](https://gyazo.com/632295ab455798906a43c34506fa0472)

こんな感じ。
一応必要な要件は満たしてる。

# DDU使ってみる

DDUを使ってみよう。
というか検索してもほとんどこれだし。

## DDUってなーに

Display Driver Uninstallerです。

普通にドライバアンインストールすると、いろいろ残ったりするんですが、こいつは跡形もなく消し去ってくれます。
グラボ周辺の機能問題で異常が出たときはこれをやるといいっていうのがセオリーみたいです。

## 使い方

以下の記事を参照に。
私は一応セーフモードにしました。

[【Shadowplay】録画が機能しなくなった時の対処法一例 \- 暇人雑記](http://www.himajin-block30.com/entry/2018/12/01/165457)

# 結果

とりあえず動いてる

まぁいつも、数回録画できてからいきなり不可になるので、今後どうなるかはわかりません。
もしも問題起きたら追記するので、追記がなかったら問題がなかったということです。

