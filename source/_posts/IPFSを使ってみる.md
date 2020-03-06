---
title: IPFSを使ってみる
date: 2020-02-15
---

## IPFSって何？

> インターネット上の情報も同様です。同一の内容であればどのサーバ上から取得したか？どの名前のファイルから取得したかなどという入手先はほとんどの場合で重要ではありません。そのためその情報の「場所」ではなく、「こういう内容の情報」というコンテンツの内容自体を直接指定して情報にアクセスする仕組みを考えることができます。これが「コンテンツ指向」になります。
>
>
> 引用: https://ipfs-book.decentralized-web.jp/what_is_ipfs/

要するに、トレントみたいに世界に大量のサーバー置いてウェブサイトとかアプリケーションとか公開しようぜ！って感じですかね。

→つまりIPFS入れてる人みんながサーバーになるということ

「セキュリティは？」って思うかもしれませんが、そこはハッシュ値で厳重に管理されているので改ざんの心配はなさそうです。



## 使ってみよう

[![Image from Gyazo](https://i.gyazo.com/79b6f2f7b06c994839923c843e239d8b.png)](https://gyazo.com/79b6f2f7b06c994839923c843e239d8b)

[公式のGithubページ](https://github.com/ipfs-shipyard/ipfs-desktop)から実行ファイルを落としましょう
ちなみにこの他にもLinuxようにtar, debなどのファイルがあります。

[![Image from Gyazo](https://i.gyazo.com/703e5b4b43134977390b59c60c5de8c3.png)](https://gyazo.com/703e5b4b43134977390b59c60c5de8c3)

インストールは全部日本語です。
基本次へでおｋ

[![Image from Gyazo](https://i.gyazo.com/b1dee1b05e5a3f694d8f72237edc8a92.png)](https://gyazo.com/b1dee1b05e5a3f694d8f72237edc8a92)

初期状態ではIPFSのファイルPINに入っていました。

[![Image from Gyazo](https://i.gyazo.com/6d5941dab092bdc1bee7a551443b5fac.png)](https://gyazo.com/6d5941dab092bdc1bee7a551443b5fac)

こんな感じで接続状態も確認できました。

[![Image from Gyazo](https://i.gyazo.com/c5a691489c6d9733f7517521c4a392b9.png)](https://gyazo.com/c5a691489c6d9733f7517521c4a392b9)

2分ほどでアクセスがここまで増えました。
大きいファイルをホストするとより多くの帯域を使いそうですが、今の所は許容範囲ですかね...

[![Image from Gyazo](https://i.gyazo.com/a09f073101d6d7ff5dff4aefdad836f9.png)](https://gyazo.com/a09f073101d6d7ff5dff4aefdad836f9)

残念ながら日本語対応はしてませんでした。



## ウェブサイトを公開する

[![Image from Gyazo](https://i.gyazo.com/264b9234d28696eb76b380b85a836348.png)](https://gyazo.com/264b9234d28696eb76b380b85a836348)

こんな感じのカスみたいなサイトを作りました

[![Image from Gyazo](https://i.gyazo.com/e1c0233a77faafe794508ae0549de473.png)](https://gyazo.com/e1c0233a77faafe794508ae0549de473)

ローカルで表示するとこうです。
これを今から公開しましょう。

[![Image from Gyazo](https://i.gyazo.com/a0f169a400343f84dfb5fca501ef8e20.png)](https://gyazo.com/a0f169a400343f84dfb5fca501ef8e20)

さっきのクソサイトはこのtestフォルダに入っています。

`ipfs add -r test/`を実行しすると、フォルダ内部のすべてのファイルをアップロードします。

この際、前まで必要だったpinする動作が不要になっているようです。

[![Image from Gyazo](https://i.gyazo.com/12e481d21c934764ae3a235cae47ad46.png)](https://gyazo.com/12e481d21c934764ae3a235cae47ad46)

このように、勝手にpinされていました。

[![Image from Gyazo](https://i.gyazo.com/e3af1d8138ec828b7af1715c72b7da89.png)](https://gyazo.com/e3af1d8138ec828b7af1715c72b7da89)

右クリックしてリンクを取得しましょう

[![Image from Gyazo](https://i.gyazo.com/252599ff9bc54c2c8d5e14269f62a626.png)](https://gyazo.com/252599ff9bc54c2c8d5e14269f62a626)

ipfs.ioのドメインでホストされていることが確認できました。



## 独自ドメインを使ってみる

このクソサイトに独自ドメインを付けてみましょう。
今回はtest.m86.workを付けたいと思います。

ドメインの設定ですが、オススメはCloudFlareです。
理由はSSL通信ができるから。

ネームサーバーを変更していない人はCloudFlareに変更してもいいかも

[![Image from Gyazo](https://i.gyazo.com/7113676df233505370063c41ba2fb577.png)](https://gyazo.com/7113676df233505370063c41ba2fb577)

まずはCNAME。Nameに設定したいドメインを、Targetには`ipfs.io`を指定。
SSL通信を利用したい人はProxiedにしておきましょう。

![img](https://gyazo.com/0a6d0340d09e89e5df0cc561557f392d.png)
https://gyazo.com/0a6d0340d09e89e5df0cc561557f392d

次にTXTですが、こちらのipfs.io以下をコピーしてください。

[![Image from Gyazo](https://i.gyazo.com/9bc05a501ae26da076085d7ffb5a9d89.png)](https://gyazo.com/9bc05a501ae26da076085d7ffb5a9d89)

次にNameを好きなドメイン、Contantに`dnslink=[さっきコピーしたやつ]`を貼ります。

これで

[![Image from Gyazo](https://i.gyazo.com/a8fef6f65ff289b98b53d3f9de4bd89b.png)](https://gyazo.com/a8fef6f65ff289b98b53d3f9de4bd89b)

test.m86.workでクソサイトに接続できるようになりました。



SSLもやりましょう。

[![Image from Gyazo](https://i.gyazo.com/88dc719b12a8e5abb2d94956d433a2e1.png)](https://gyazo.com/88dc719b12a8e5abb2d94956d433a2e1)

といってもここをflexibleにするだけです。



## まとめ

なんとなく使ってみましたが、普通に楽しかったです。
いろいろできそうなのでまたいじっていきたいと思ってます。