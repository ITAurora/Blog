---
title: js中的BOM基础
date: 2020-11-24 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/16.jpg
banner_img: ../articleImages/16.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
	</head>
	<body>
		
	</body>
</html>
<script type="text/javascript">
/*
 BOM Browser object model 浏览器对象模型!!!
 BOM是由一系列对象组成,每个对象都有自己的属性和方法,用来管理浏览器窗口与窗口之间的通信!!!
 重点:
 window是BOM中的顶层(核心)对象,所有的对象都是通过它延伸出来的!!!
 由window延伸出来的对象有:
 1.doucument
 2.hsitory
 3.location
 4.navigator
 5.screen 
 6.frames(已经被弃用,可忽略!只要在老的网站源码中可能会见到!!)
 
 window特点:
 所有的全局变量,都是window的属性!
 所有的全局函数方法,都是window的方法!!
 在使用window的子对象/属性,可以省略window!!
 */
//举例子!!!!!!!!!!!!!!!!!!!!!!!!
var a = 10;
console.log(a);
//其实a 就是window的属性
console.log(window.a);
function sum(a, b){
	console.log(a + b);
}

sum(10, 20);
//也可以
window.sum(99, 778);
//定义变量名  不要使用top  因为top表示的就是顶层对象window
console.log(top);
console.log(window);  //window对象
console.log(self); //self关键字  永远指代window对象!!!
//-------------
//平时我们访问document
console.log(document);
console.log(window.document);//一般可忽略window
console.log(document.body);
console.log(window.document.body);//一般可忽略window

</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/155155c650a34ce097d57e8adab09b14.png)

