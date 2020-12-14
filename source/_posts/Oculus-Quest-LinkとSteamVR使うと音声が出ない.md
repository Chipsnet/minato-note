---
title: Oculus Quest LinkとSteamVR使うと音声が出ない
date: 2020-12-14 22:20:19
tags:
    - VR
    - Oculus Quest
categories: 不具合
---

おれ「Oculus LinkでVRChatたのし～～～～！」

おれ「あれ・・・・？」

＿人人人人人人人人人＿      
＞　**声が入ってねぇ**　＜      
￣Y^Y^Y^Y^Y^Y^Y^Y^Y^￣

Oculus Linkを使用していると、Oculus Virtual Audio Deviceっていうのからマイクが入るんですが、これがVRChatで全く反応しない。

# 調べてみた

Oculus公式サイトにありました

[![Image from Gyazo](https://i.gyazo.com/676135230358680061b37435e8f80bec.png)](https://gyazo.com/676135230358680061b37435e8f80bec)

> A. Oculus Linkを使用しているときに、マイクがボイスチャットで機能しません。       
> Q. Oculus LinkでQuestを使用すると、OculusQuestマイクが現在正しく機能していません。 今後数回のアップデートでこれを修正する予定です。
> [Oculus Linkのトラブルシューティングのアドバイス](https://support.oculus.com/572216283519517/)
 
結果、**既知の問題**でした。        
つまりどうやってもなおんねぇということらしい。

# 治し方（治るかもしれない）

とりあえずいろいろ調べたり自分でやってみて、以下の解決法をやればそこそこの確率で治りました。

- `Oculusソフトウェア > 設定 > ベータ > Oculusを再起動` を実行して、Oculusの諸々を再起動
- Steam VRを経由せずにVRChatを起動（なぜかSteam VR経由より激重だけどマイクの動作率は結構高い）
- ひたすら音声が出るまでOculus Linkをやりなおし

こんな感じです。        
パッとするものは正直ないっすわ

修正を待つしかなさそうですねオワオワリ