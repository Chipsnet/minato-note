---
title: Google Drive FileStream上でYarnは使えない
date: 2020-07-24 01:42:38
tags:
    - Node.js
    - Yarn
categories: 不具合
---
Google Drive File Stream（以下DriveFS）、知ってますか？
GSuiteの人限定で使える、Google Driveを外部ストレージとしてマウントするソフトウェアです。

GSuiteのプランでGoogle Driveを無制限で使用できるようにしておけば、PCの容量を気にせず作業できるので、非常に便利で重宝しています。

# DriveFS上でYarnを使いたい

Yarn Pkg（以下Yarn）は、Node.jsのパッケージ管理ソフトです。
npmとかありますが、僕はYarn派です。

んでそのYarnなんですが、DriveFS上で使いたいんですよ。
てかこれ使えないとNode.jsアプリケーション開発できないし。

結論から言うと、無理です。

# DriveFS上でYarnは使えない

`yarn install`を実行すると、以下のエラーが発生します。

```bash
error An unexpected error occurred: "EEXIST: file already exists, mkdir 'G:\\path-to-repos\\node_modules\\@electron\\get\\node_modules'".
info If you think this is a bug, please open a bug report with the information provided in "G:\\path-to-repos\\yarn-error.log".
info Visit https://yarnpkg.com/en/docs/cli/install for documentation about this command.
```

ファイルは既に存在しますというエラーですが、おそらくダウンロードされたファイルから順番にDriveFSによって処理されていくので、それでファイルチェックの整合性が取れなくなっているんじゃないかと思います。

兎にも角にもDriveFSでYarnは使えません。残念。

ちなみに、pipとかは依存関係のインストールをリポジトリフォルダ内ではなくPC内に行うので、PythonとかはDriveFS内で作業できます。

たぶんnpmも同じ感じで依存関係インストールするので、npmもDriveFS内で使えないと思います。はい。

> 追記:
> npmも使えませんでした。