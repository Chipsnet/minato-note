---
title: Misskey（めいすきー）で検索を有効にする覚書
date: 2021-10-05 02:54:26
tags:
    - Misskey
    - Node.js
    - 自宅鯖
categories: 技術
---

こんにちは。        
実は私、OpenWorld.netというMisskeyサーバーを運営しています。

だいぶ前に検索を有効にしたのですが、なにかの拍子で無効になっちゃったみたいなので、有効にするメモです。

Misskeyについて知りたい人はここへ

https://join.misskey.page/ja-JP/

<!--more-->

# 前提

この記事はめいすきー（Misskeyのフォーク）での方法です。     
通常のMisskeyでの方法は知りません。

めいすきーはこちら      
https://github.com/mei23/misskey

# 環境

- Ubuntu 20.04.3 LTS

# MeCabの導入

```bash
sudo apt install -y mecab mecab-ipadic-utf8
```

以上のコマンドでMeCabを導入します。

# Configファイルをいじる

`misskey/.config/default.yml`を開きます。（nanoとかで大丈夫です）

```yml
# Mecab検索インデックス 使用する場合は以下を指定
#mecabSearch:
#  # mecabパス
#  mecabBin: mecab
#  # mecab辞書 (オプション)
#  mecabDic: /usr/lib/x86_64-linux-gnu/mecab/dic/mecab-ipadic-neologd
```

以上の箇所を以下のように変更します。

```yml
# Mecab検索インデックス 使用する場合は以下を指定
mecabSearch:
  # mecabパス
  mecabBin: mecab
#  # mecab辞書 (オプション)
#  mecabDic: /usr/lib/x86_64-linux-gnu/mecab/dic/mecab-ipadic-neologd
```

完了したら以下のコマンドで再起動します。

```bash
sudo systemctl restart misskey
```

![](https://i.gyazo.com/91efae6d1f98b4d50bb27a71974467d5.png)

こんな感じで検索ができるようになりました！

# 注意点

検索を有効にした時点から検索できるようになるので、検索を有効にする以前の投稿は検索することができません。        
なので新しいインスタンスを立てたら早めに有効にしましょう。