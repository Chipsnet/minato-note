---
title: TailwindCSS + Nuxt.jsで、ホットリロード（自動更新）が機能しない
date: 2021-10-06 20:10:12
tags:
categories:
---

Nuxt.js を利用してサイトを制作すると、やはりホットリロードが便利だな、と感じます。  
まぁ最近はどのフレームワークにもあるのですが、これがないともうサイト制作できません。

しかし、Tailwindcss を利用していると、ホットリロードが機能しなくなってしまいました。

その原因は `<style></style>` タグでした。

この記事は、この事象を解決するためのメモです。

<!--more-->

# 原因

Hot reload not working in Nuxt Js when ＜ style ＞ is in index.vue page : Nuxt — https://www.reddit.com/r/Nuxt/comments/p3tg9t/hot_reload_not_working_in_nuxt_js_when_style_is/

この reddit によると、index.vue に style タグがあるとホットリロードが動作しない、とのことです。

https://github.com/nuxt-community/tailwindcss-module/issues/357#issuecomment-861749855

この issue でも、同じく style が原因だと指摘しています。  
style タグが原因なのは間違いないみたいです。

# index.vue 以外ではどうか

Reddit では、「index.vue」に style があると動作しない、と書かれています。  
ではそれ以外（layouts, pages, components）ではどうでしょうか？

結果：そもそもホットリロードが動作しないのは `index.vue` だけっぽい

| style タグの状態                            | 場所      | ホットリロード |
| ------------------------------------------- | --------- | -------------- |
| index.vue なし, layouts あり                | index.vue | ○              |
| index.vue あり, layouts あり                | index.vue | ✗              |
| index.vue あり, layouts あり                | test.vue  | ○              |
| index.vue なし, layouts あり, test.vue あり | test.vue  | ○              |
| index.vue あり, layouts あり, test.vue なし | test.vue  | ○              |

えー、まとめますと

**index.vueにいるときに、index.vueにstyleタグがあると動作しない** ということです。

# 対策1: index.vueにstyleタグを置かない

前述の検証結果の通り、要はindexにstyleタグを置かなきゃいいわけです。        
例えばlayoutsのstyleをscopedにしないで、layoutsからindexにcssを適用するとか、やりようはありそうですね。

# 対策2: バージョンを下げる

https://github.com/nuxt-community/tailwindcss-module/issues/357#issuecomment-863390714

このissueのコメントにある通り、tailwindcssとpostcssを下げることで、この問題は解決できます。

しかし、最新のtailwindcssで使えるクラスのいくつかが使えなかったりするので、将来この問題が解決された場合に最新版に対応できません。

私も一回バージョン下げてみたんですが、このバージョンのtailwindcssでは `text-6xl` までしか無いようで、それ以上を指定してたやつが全滅してました。

なのであんまり、おすすめはしないかなー...

一応、dependenciesのpostcss, tailwindcssを

```json
{
    "@nuxtjs/tailwindcss": "~3.4.3",
    "postcss": "~7.0.36",
}
```

こんな感じのバージョンに設定してあげればこの方法を試すこともできます。

yarnを使ってる場合は `node_modules` と `yarn.lock`を削除したあとに

```bash
yarn install
```

を実行してください。

# 対策3 `@nuxtjs/tailwindcss` を使わない

PostCSS7互換性ビルドを使用します。

https://tailwindcss.com/docs/installation#post-css-7-compatibility-build

tailwindcssの公式サイトに記載があります。       
ただこれは結構難しそうだったので、分かる人だけやってみてください。

関連のissue項目を置いておきます。

https://github.com/tailwindlabs/tailwindcss/issues/4962#issuecomment-880817896      
https://github.com/nuxt-community/tailwindcss-module/issues/357#issuecomment-906897293

この方法のサンプルリポジトリ        
https://github.com/bradlc/jit-nuxt

# 対策4? JITモードを有効にする

`tailwind.config.js`のモード指定をJITにすると直る、という情報を見かけました

が、やってみたところ特に改善している様子はなさそう...?      
よくわかりませんが、これは無理そうです。

動作報告あればお待ちしています。

# おわりに

Issueには、次バージョンへの対応のためこれらのIssueは無視されている、と書いてありました。        
おそらく修正されるまではまだ時間がかかると思われます。

ですが、納期は待ってくれないので、これらの対応で凌ぎましょう。

以上です。