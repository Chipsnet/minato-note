---
title: Hexoでテーマの設定ファイルをGithubで保持する方法
date: 2020-09-24 01:46:38
tags:
    - Github
categories: 技術
---

こんにちは、巳波みなとです。

このブログ、Hexoという静的サイトジェネレーターで生成、GithubPagesでホストしているのですが、これらのテーマ設定が少し厄介だったので紹介します。

# テーマのインストールの仕組み

テーマがインストールされるとき、サイトファイルのthemesの中にファイルが保存されるんですが、それは「Git submodules」という仕組みで管理されています。

この中で行われた変更は、なんと自分のリポジトリにコミットすることができません。

これはどういうことかというと、テーマに関して設定したことが、他の環境でgit cloneしたときには消えているということです。

# テーマのconfigの上書き

実は、これへの対策として、テーマの`_config.yml`ファイルを上書きする仕組みが用意されています。

[Configuration \| Hexo](https://hexo.io/docs/configuration.html#Alternate-Theme-Config)

その方法は、ルートディレクトリ（db.jsonやpackage.json、_config.ymlがあるディレクトリ）に、`_config.[テーマ名].json`ファイルを作るというやり方です。

これによって、`_confit.[theme].json`が、テーマの_configファイルよりも優先して読み込まれるように設定できます。

そんだけ