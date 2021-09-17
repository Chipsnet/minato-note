---
title: 慶安のWIN-70Bのジャンクをもらったので修理してみる
date: 2020-12-17 21:58:32
tags:
    - Windowsタブレット
categories: 技術
---
こんばんは。

インターネットフレンドの[铃宫](https://misskey.open-w.net/@suzumiya)くんから、慶安のWIN-70Bをもらったので、治してみたいと思います。

# 状態

- 通常起動可
- タッチパネル操作不可

こんな感じ。
つまりタッチパネル不良のジャンク、というわけですね。

外傷はなく、特別壊れている感じはありません。

<!-- more -->

# 推測

中華タブレットをたくさんいじってる人ならまぁわかると思うんですが、中華タブレットのタッチパネルが効かなくなる原因のほとんどが、ドライバの不足なんですよね。

特に、DoubleDriverなどを使ってもバックアップできない（個別にする必要がある）SileadTouch.fwというドライバ、これがないとタッチパネルが反応しません。

状態を聞いた時、まずこれが浮かびました。

# 準備

とりあえずドライバを揃えます。

慶安のこのタブレットは、いろんな型番で販売されているらしく、「KEM-70B」と「KVI-70B」のドライバと互換性があるみたいです。

そこでまずは、 [KEM\-70B　KVI\-70B　ドライバーはここにある！](http://afritom.blog136.fc2.com/blog-entry-549.html) さんのリンクから、ドライバとSileadTouch.fwをダウンロードしました。

# 開封

届いたので開封します（開封済みだけど）。

[![Image from Gyazo](https://i.gyazo.com/d5c529e78f017c131c9ba27429b21bcb.jpg)](https://gyazo.com/d5c529e78f017c131c9ba27429b21bcb)

こんな感じの普通のタブレットですね。

[![Image from Gyazo](https://i.gyazo.com/b624dae7a5ed6bf8dd9f56ecd38b7cf6.jpg)](https://gyazo.com/b624dae7a5ed6bf8dd9f56ecd38b7cf6)

中には保証書とマニュアルがありました。

まぁ読まなくてもどうにかなるでしょ

[![Image from Gyazo](https://i.gyazo.com/124181afd3210aee78c202c7c7a2022b.jpg)](https://gyazo.com/124181afd3210aee78c202c7c7a2022b)

外見は聞いていた通りめっちゃ綺麗でした。

とりあえず充電せずに起動してみると

[![Image from Gyazo](https://i.gyazo.com/3bee14175fb5671d0eedc23bb2471bd2.jpg)](https://gyazo.com/3bee14175fb5671d0eedc23bb2471bd2)

あっさり起動しちゃいました。

そして............やっぱりタッチは効きませんでした。そりゃそう。

[![Image from Gyazo](https://i.gyazo.com/5c80902ae6bdff0a94095b73b82af8b3.jpg)](https://gyazo.com/5c80902ae6bdff0a94095b73b82af8b3)

パソコンの情報を見てみると、タッチパネルは認識されています。

ということは、タッチパネル・ドライバは存在するようです。

# 修理編

それではやっていきましょう。

まずは環境を整えます

[![Image from Gyazo](https://i.gyazo.com/a262959fd415bca4ed555a41aee58b83.jpg)](https://gyazo.com/a262959fd415bca4ed555a41aee58b83)

充電可能なMicroUSBハブにマウスとキーボードを接続します。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">カオスになってきた <a href="https://t.co/smtSnNPmvW">pic.twitter.com/smtSnNPmvW</a></p>&mdash; Minami Minato/巳波みなと (@minatoo86) <a href="https://twitter.com/minatoo86/status/1339538786254917632?ref_src=twsrc%5Etfw">December 17, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

全部つなげるとこんな感じになりました。
カオスですね。

[![Image from Gyazo](https://i.gyazo.com/6189c54f033e60ab9005562918cbecd6.jpg)](https://gyazo.com/6189c54f033e60ab9005562918cbecd6)

まずはUSBメモリに`SileadTouch.fw`を入れ、差し込みます。

[![Image from Gyazo](https://i.gyazo.com/09f06f6458500960e61798f09f3cced1.jpg)](https://gyazo.com/09f06f6458500960e61798f09f3cced1)

それを、`C:\Windows\System32\drivers`に入れます。
この際管理者権限を求められるので許可します。

その後、再起動しましょう。

私の場合、この方法では治りませんでした。

タップは反応するようになりましたが、思い通りのところにタップされません。

そんなときは、まずコントロールパネルにアクセスして

[![Image from Gyazo](https://i.gyazo.com/a80bf85b13ae10b7ca2c52c5541da508.png)](https://gyazo.com/a80bf85b13ae10b7ca2c52c5541da508)

ハードウェアとサウンドのタブレットPC設定を開きます。

[![Image from Gyazo](https://i.gyazo.com/1da6a03d6bfd4fb5ad606e6b088dcbeb.jpg)](https://gyazo.com/1da6a03d6bfd4fb5ad606e6b088dcbeb)

そしてディスプレイオプションに「リセット」があるので選択します。

すると、使えるようになりました。
タッチ修理成功です！

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">タッチパネルジャンクタブレット、なおったわ <a href="https://t.co/joQt9Tu6wQ">pic.twitter.com/joQt9Tu6wQ</a></p>&mdash; Minami Minato/巳波みなと (@minatoo86) <a href="https://twitter.com/minatoo86/status/1339543003313008641?ref_src=twsrc%5Etfw">December 17, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

こんな感じです。

参考になりましたかね？
最後に参照したサイトを貼っておきます。

[KEM\-70B　KVI\-70B　ドライバーはここにある！](http://afritom.blog136.fc2.com/blog-entry-549.html)

[WinTab7（Win\-70B）のWindows10 大型アップデート苦戦 No\.1 \| 青猫の道草日記 \- 楽天ブログ](https://plaza.rakuten.co.jp/blucat3f/diary/201811250000/)

[Ployer MOMO7\(or MOMO8\) SileadTouch\.fw を失いタッチパネル使用不可 \- Windows10 1909 をクリーンインストールして失敗 \| ふるた技工所\(てっこうしょ\) \- 楽天ブログ](https://plaza.rakuten.co.jp/ftechworks/diary/202001160001/)

[KEIAN KVI\-70B ドライバ保管庫 \| Windows 高速化,EeePC,ネットブック カスタマイズ・改造・便利なオプション紹介](http://eeepc.dnki.co.jp/?eid=1106892)

[価格\.com \- KEIAN KEM\-70B のクチコミ掲示板](https://bbs.kakaku.com/bbs/K0000789714/#19191083)