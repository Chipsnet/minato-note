---
title: Lubuntu 19.10 LXQtでカバーを閉じるとWi-Fiが切断される問題
date: 2020-03-05 12:34:04
tags: ["Lubuntu", "LXQt"]
categories: ["技術", "不具合"]
---

ノートPCにて、Lubuntu 19.10でカバーを閉じるとWi-Fiが勝手に切断される問題が発生したので解決法を共有します。

# 確認

- 電源管理から、カバーが閉じても何も起こらない設定にする
- `/etc/systemd/logind.conf`の`HandleLidSwitch`がignoreになっている
  - コレやってない場合は[ここ](https://www.yokoweb.net/2018/05/11/ubuntu18-notepc-suspend-ignore/)を参考に設定

# システムログを見る

私の場合は上記方法でも解決できなかったので、他の方法を模索しました。
まずはシステムログを見ます。

`/var/log/dmesg`を見ます。

すると、ログの中に

` Started Load/Save RF Kill Switch Status. `というログを見つけました。

どうやらRF Killというものが働いて問題が起こっているようです。

# RF Killは消せない

これ、どういう仕組かは知りませんが、aptから削除しても作動します。
おそらくシステムの一部なのかな～と思います。

Linuxでwlanを使えるように頑張ってみた - Folioscope http://folioscope.hatenablog.jp/entry/2013/03/26/232921#

Raspbian Stretch Lite で突然無線LANに接続不能になったとき - 今日も微速転進 https://a244.hateblo.jp/entry/2017/12/28/024238

上記サイトでは、コレに関する解決法を掲載していました。
しかし私はこれでは治りませんでした。

# 物理的な原因だった

原因は、**本体のワイヤレススイッチがONになっていた**でした。

OFFならわかるけど、ONって・・・・

わかるわけないだろ！！！！！！！！！！！！！！！！！！！

と、いうわけで、どういうことかは知りませんが、あっさりと治ってしまいました。
コレのせいで2日潰れたけどね