---
title: Raspbianで起動時処理を簡単に実装する
date: 2020-03-02 22:28:49
tags: 技術
---



私、めんどくさいのが大嫌いなので、超簡単に起動時処理を実装します。

ほとんどの記事ではlocal.rcで実装してたんですが、rootで実行されるのとうまくいかなかったので今回はcronで実装します。

## raspi-configの設定

まずは、ネットが接続されるまで処理を待つ設定をします。

（これをしないと正常に動作しないときがあるみたい）

[![Image from Gyazo](https://i.gyazo.com/56439f0ba30a869d8c1fe7a73a84fb91.png)](https://gyazo.com/56439f0ba30a869d8c1fe7a73a84fb91)

`sudo raspi-config`を入力

[![Image from Gyazo](https://i.gyazo.com/a948e12d11adbd8f49ad45b2f623b44e.png)](https://gyazo.com/a948e12d11adbd8f49ad45b2f623b44e)

Boot Optionsを選択

[![Image from Gyazo](https://i.gyazo.com/2413e127a71c44c27d86b1096519ef82.png)](https://gyazo.com/2413e127a71c44c27d86b1096519ef82)

Wait for Network at Bootを選択

[![Image from Gyazo](https://i.gyazo.com/98b1ab3d7834ed281b4442edf8779717.png)](https://gyazo.com/98b1ab3d7834ed281b4442edf8779717)

はいを選択

[![Image from Gyazo](https://i.gyazo.com/96f182577ba2f6de15e61e110cda42bb.png)](https://gyazo.com/96f182577ba2f6de15e61e110cda42bb)

了解を選択

これでOK

## crontabのログ設定

実行されているか確認するために、ログが残るよう設定しましょう。

`sudo nano /etc/rsyslog.conf`

でファイルを開き

`#cron.* /var/log/cron.log`

と書いてある行を見つけて、#を外します（コメントアウト）

`cron.* /var/log/cron.log`

あとはCtrl+Xを押して、保存するか聞かれるのでyを押す。
終わったらログの設定は完了です。

## crontabの設定

crontabには@rebootという、起動時に処理されるトリガがあり、今回はこれを利用していきます。
raspbianには標準で備わっているので、利用していきましょう。

`crontab -e`で編集します。

初回はどのエディタを使うか確認されます。nanoでよければEnterを、他がよければ数字で選択してください。
（私はnano使いなのでそのままEnter）

そしたら、nanoが起動して編集可能になるので、一番下に`@reboot [実行したいコマンド]`を追記してください。
今回はVNCサーバーが起動時に立ち上がるようにしたかったので、`@reboot vncserver -localhost no`を追記しました。

そしたら保存して、`crontab -l`で今入力した内容があるかを確認してください。

## 再起動

再起動して実行されていればOK。

## 実行されていなかった場合

しっかりcrontabが動いているかはログで確認できます。

`sudo cat /var/log/cron.log`を確認して、エラーだったり、入力したコマンドがないようでしたら検索してみてください。

こんな感じで簡単に実装できました。やったぜ。