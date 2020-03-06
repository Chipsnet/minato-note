---
title: lubuntu 19.10 LXQtにVNCで接続する
date: 2020-03-03 21:52:25
tags: 技術
---

Lubuntu 19.10をインストールしたのですが、そこでVNCを使う際つまずいたので覚書。

いつもは`tigervnc-standalone-server`というパッケージを利用しているのですが、LXQtに対応していないのかは知りませんがバグりまくって使い物にならなかったので、今回は別の手段でやっていきます。

## X11VNC Serverを使う

まずはインストールです。

`sudo apt install x11vnc`でx11vncをインストールします。
その後、`x11vnc -storepasswd`と入力するとpasswordを聞かれるので、好きなものを指定してください。

最後に`x11vnc`と打って実行すると、vncサーバーが立ち上がります。

あとは簡単、他のPCからローカルIPを使って接続すればおｋです。

ただ、terminal閉じるとサーバーも閉じちゃうので、screenとかで実行したほうがいいと思います。