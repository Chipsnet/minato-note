---
title: ウチのWifiが異様の遅いのでどうにかしてみる
date: 2020-03-02 20:23:28
tags: ["ネットワーク", "Wi-Fi"]
categories: ["技術"]
---

私の家には3つのSSIDがあって

| SSID       | 周波数 |
| ---------- | ------ |
| pr500m-*-3 | 5GHz   |
| pr500m-*-1 | 2.4GHz |
| MyPlace_*  | 2.4GHz |

という3つのWi-FiのSSIDがあります。

上のpr500mから始まる２つは、NTTから貸し出しされている「PR500MI」というルーター（ONUの機能も持っている）から出ているWi-Fiです。

下のMyPlaceは、Fonというルーター（ちょっと特殊なやつ）の電波です。
（まぁ今回はFonはあんまり関係ないです。）

そして、**PR500MIの2.4GHzが異様に遅い。**

記憶では、使い始めは結構早かったと思うんですよ。
でも異様に遅い。

速度を測定すると

[![Image from Gyazo](https://i.gyazo.com/466cf818ded75c6a353f9265c87bff73.png)](https://gyazo.com/466cf818ded75c6a353f9265c87bff73)

こんな感じ。

「家のネットが遅いんじゃないの？」とお思いのアナタ。

[![Image from Gyazo](https://i.gyazo.com/080b3ca15a6ae41f79e22a589cdb1950.png)](https://gyazo.com/080b3ca15a6ae41f79e22a589cdb1950)

5GHzはこんな感じ。

「流石に差がありすぎじゃない？」

と思ったので、なんとかしてみようと思います。

## チャンネルの設定

[![Image from Gyazo](https://i.gyazo.com/b5b4309022daad7d04d2184975b74b5d.png)](https://gyazo.com/b5b4309022daad7d04d2184975b74b5d)

とりあえずチャンネルがこのように設定されているので、競合していないチャンネルを探します。

それに使用するのは、[WiFi Analyzer](https://www.microsoft.com/ja-jp/p/wifi-analyzer/9nblggh33n0n#activetab=pivot:overviewtab)というWindowsアプリケーションです。

[![Image from Gyazo](https://i.gyazo.com/24d88856d55a167bcbefe21f12f949a7.png)](https://gyazo.com/24d88856d55a167bcbefe21f12f949a7)

現在はこのようになっています。

[![Image from Gyazo](https://i.gyazo.com/c3fe9811b97a5ff3d0acf451d610d569.png)](https://gyazo.com/c3fe9811b97a5ff3d0acf451d610d569)

現在はCH1ですが、これは他のWiFiと干渉しているようです。

[![Image from Gyazo](https://i.gyazo.com/25977972f9d5c8d9359fd3d0684512e6.png)](https://gyazo.com/25977972f9d5c8d9359fd3d0684512e6)

ですので、CH3に変更してみました。

さらに、pr500mには2というアクセスポイントもありますが、通常使用しないので無効にしてみます。

[![Image from Gyazo](https://i.gyazo.com/00ee799fd91fb27ea011bc6ec39ca0f0.png)](https://gyazo.com/00ee799fd91fb27ea011bc6ec39ca0f0)

結果、通信速度が2ケタになるようになりました。

これでまぁ実用的に使えるようになってしまったので、とりあえず大丈夫としましょう。

チャンネル変更、結構効果ありました。お試しあれ。