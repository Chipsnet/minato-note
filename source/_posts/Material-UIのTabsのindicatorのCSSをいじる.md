---
title: Material UIのTabsのindicatorのCSSをいじる
date: 2020-07-09 03:28:40
tags: 
    - Node.js
    - React
    - CSS
categories: 技術
---
```jsx
const StyledTabs = withStyles({
    indicator: {
        display: "flex",
        justifyContent: "center",
        backgroundColor: "transparent",
        "& > span": {
            maxWidth: 0,
            width: "100%",
        },
    },
})((props) => <Tabs {...props} TabIndicatorProps={{ children: <span /> }} />);
```

こんな感じ
上記はindicatorのmaxWidthを0にして消してます

あとは通常`<tabs></tabs>`なところを`<StyledTabs></StyledTabs>`に変える
これでおｋ

基本的にはリファレンスとかに書いてあります
以下参考ページ

[Tabs React component - Material-UI](https://material-ui.com/components/tabs/#experimental-api)
[Tabs API - Material-UI](https://material-ui.com/api/tabs/)