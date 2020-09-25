---
title: iPhone版Braveからいつの間にかBrave Syncが消えてた
date: 2020-09-26 01:09:03
tags:
    - ブラウザ
categories: 不具合
---
こんばんは。

[Braveブラウザ](https://brave.com/min233)には、Brave Syncというブックマークなどを同期する機能があります。

パソコンだとこんな感じで

[![Image from Gyazo](https://i.gyazo.com/0bc8b0577da481a126b95f81526b799d.png)](https://gyazo.com/0bc8b0577da481a126b95f81526b799d)

デバイスリストとかを確認することができるようになっています。        
実はこれ、iPhoneにもあったんですが、気づいたら消えてました。

# 確かに様子がおかしかった

PCとiPhoneを同期させようとしたら、なぜか過去に同期したわけわからないものがiPhoneにだけ同期されて、PCの同期チェーンには入ってないなんてことがありました。

# いつ消えたんや

[![Image from Gyazo](https://i.gyazo.com/072163b4437e6fcfb7e742ede86d5afb.png)](https://gyazo.com/072163b4437e6fcfb7e742ede86d5afb)

公式サイトのRelease noteを確認すると、消えたのは最新のリリースみたいです。      
（つい最近だった）

Temporary disable the Sync UI until Sync V2 · Issue #2718 · brave/brave-ios https://github.com/brave/brave-ios/issues/2718

どうやらissueによると、現在Brave Syncにはv1とv2があり、今までiPhoneに搭載されていたのはおそらくv1だったんだと思います。

たぶんv1はスマホでしか正式リリースされてないです。      
PCのBrave Sync v1はflagsから有効にできたあれじゃないですかね。

上で紹介した不具合も、恐らくv1とv2でうまく同期できてなかったんじゃないですかね      
だからv1の時にPCで同期したデータがiPhoneに同期されてたんじゃないかなーと

兎にも角にも、v2のiPhone上陸を待つしかなさそうですね。