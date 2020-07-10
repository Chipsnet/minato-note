---
title: Google Cloud SDKでUnicodeEncodeErrorが出る
date: 2020-07-10 22:02:51
tags:
    - GoogleCloudPlatform
    - GitBash
categories: 不具合
---
> はてなブログで過去に公開した記事を移行しました
> 元リンクはこちら https://minato86.hatenablog.com/entry/2019/12/06/025130

こんなエラーが出た

`ERROR: gcloud crashed (UnicodeEncodeError): 'ascii' codec can't encode characters in position 3-8: ordinal not in range(128)`

エラーから察するに文字コード系のエラーっぽい。

このエラーはGAEにデプロイする時やGCSDKのアップデートをする時とかに出るっぽい。

## 原因

何故かWindowsのPowerShellで`gcloud`コマンドを使用すると`ascii`を使ってしまうらしい。    
それが悪さしてるっぽい

## 解決策

Git導入してGitbashを使いましょう

