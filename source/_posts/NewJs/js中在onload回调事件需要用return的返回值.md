---
title: 关于开启弹性盒子之后当只有文本内容的和单独存在时内容无法撑起宽度从而对齐的解决方案
date: 2022-7-06 10:10:10
tags:
  - JS
categories:
  - JS问题
index_img: ../tnt/14.jpg
banner_img: ../tnt/14.jpg
excerpt: 摘要
---

突然想起来这种情况，这种情况就是开启弹性盒子后如果一个盒子里只有纯文本内容，你的盒子是撑不起来的，这时给宽度也会无效（除非取消弹性盒子）

给你的子盒子宽度加max-content属性：

意思是盒子宽度由内容撑起
```javascript
width: max-content;
```
同时它还有其他操作


以最大的内容的宽度为盒子的宽度

```javascript
width: min-content;
```

宽度固定，内容会自适应高度
```javascript
width: fit-content(100px);
```