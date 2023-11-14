---
title: 关于cookie的获取设置和修改
date: 2022-01-10 10:10:10
tags:
  - JS
categories:
  - JS问题
index_img: ../tnt/7.jpg
banner_img: ../tnt/7.jpg
excerpt: 摘要
---


新增名为name的cookie和有效时间
```js
setCookie (name, value, expiredays) {
 
    var exdate = new Date();
 
    exdate.setDate(exdate.getDate() + expiredays);
 
    document.cookie = name + "=" + value + ((expiredays == null) ? "" : ";expires=" + exdate.toGMTString());
 
};
```
获取名为name的cookie的值

```js
getCookie(name) {
	var arr, reg = new RegExp("(^| )" + name + "=([^;]*)(;|$)");
	if (arr = document.cookie.match(reg)){
   		return (arr[2]);
  	}else{
		return false
	}
 }
```
删除为name的cookie

```js
export function delCookie (name) {
	var exp = new Date();
	exp.setTime(exp.getTime() - 1);
	var cval = getCookie(name);
	if (cval){
	 	document.cookie = name + "=" + cval + ";expires=" + exp.toGMTString();
	}
};
```
操作完想要达到token失效的效果只需要

```js
location.reload()
```
