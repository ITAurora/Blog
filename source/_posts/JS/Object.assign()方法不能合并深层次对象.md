---
title: Object.assign()方法不能合并深层次对象
date: 2021-10-15 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../tnt/3.jpg
banner_img: ../tnt/3.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

我们只知道Object.assign()方法能合并对象，已存在键的会对其进行更新，不存在的会新增并合并生成一个新对象
但是 Object.assign()方法合并只适用于单层对象
多层对象并不适用
比如：单层对象

```js
const _form = {
  site: "",
  type: "",
  author: "",
  bk: "",
  info: "",
  domain: "",
};
```
比如：多层对象

```js
const _listQuery = {
  data: {
    key: "",
    qyid: "",
    type: "",
  },
  p: {
    page: 0,
    pageSize: 0,
    total: 0,
  },
};
```
举个例子：

```js
var a = {a: {b: 1, c: 2}}
var b = {a: {b: 1, c：2}，d：3}
var c=Object.assign(a, b)
console.log(c)
```
输出结果会是{ a: { b: 1, c: 2 } ，d：3}
而不是我们想要的这样的 { a: { x: 1,z:3, y: 2 }，d：3 }
我们可以找个替代品来实现对象的深层合并（看别的大佬写的代码）

```js
var _ = require("lodash");
var a = {a: {b: 1, c: 2}}
var b = {a: {b: 1, c：2}，d：3}
console.log(_.merge(a, b));
console.log(a);
```
这样有个缺点：
就是Object.assign()方法是单层深拷贝
而这个方法是在a的值的基础上进行更改
