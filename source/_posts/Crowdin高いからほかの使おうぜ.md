---
title: Crowdin高いからほかの使おうぜ
tags: ["Github", "Crowdin"]
categories: ウェブサービスレポート
date: 2020-06-20 01:58:34
---

Crowdinは、リポジトリのファイルを翻訳とかできるやつなんですけど     
クソ高いので他のやつないか模索してみた

Github MarketPlace見てみると

- Crowdin
- POEditor
- GitLocalize

があった。

1プロジェクトの最低価格的には以下のような感じ

| アプリケーション | プラン名 | 文字列数 | 価格      |
| ---------------- | -------- | -------- | --------- |
| Crowdin          | Micro    | 500      | $16/month |
| POEditor         | Free     | 1000     | -         |
| GitLocalize      | -        | -        | -         |

こんな感じ。

GitLocalizeは完全無料っぽいけどサポートしてるファイルが少なそう。
現時点では

- Markdown
- PO（なにこの拡張子）
- JSON
- HTML
- YAML
- Localizable Strings（iOS）

に対応してるっぽい。

とりあえず完全無料っぽいのでGitLocalizeをテストで使ってみる。

サイトにアクセス

GitLocalize - Continuous Localization for GitHub Projects https://gitlocalize.com/

Githubアカウントでログインする

[![Image from Gyazo](https://i.gyazo.com/5bb2317875f600a03702222f0eb1632d.png)](https://gyazo.com/5bb2317875f600a03702222f0eb1632d)

こうなった。

そしたらAdd repository

[![Image from Gyazo](https://i.gyazo.com/887ebb26d82221944c7b4fd63893fdaf.png)](https://gyazo.com/887ebb26d82221944c7b4fd63893fdaf)

リポジトリを設定

[![Image from Gyazo](https://i.gyazo.com/d7564d5091f6fd1ff4161d0c64c546e9.png)](https://gyazo.com/d7564d5091f6fd1ff4161d0c64c546e9)

ターゲットパスを設定

あとはGithubと連携すれば設定は完了です。
かんたんですね。

[![Image from Gyazo](https://i.gyazo.com/b1aab64acbfc0c6f0683a67e0d1ec7cc.png)](https://gyazo.com/b1aab64acbfc0c6f0683a67e0d1ec7cc)

必要な機能は一通り揃っています。
正直これくらいあれば随分という気がする。



結論: Crowdinにお金払わなくてもGitLocalizeでそこそこやっていける

2020年6月21日追記：

そういえばGitLocalizeはログイン＋メンバー登録必須でした     
不特定多数からコントリビュート受けることはできないっぽい