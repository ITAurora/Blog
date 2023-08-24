---
title: 前端js元素style的样式操作
date: 2020-11-19 12:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/8.jpg
banner_img: ../articleImages/8.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			div{
				width: 300px;
				height: 300px;
				text-align: center;
				background-color: yellow;
				line-height: 150px;
				margin: 60px auto;
				font-size: 40px;
			}
		</style>
	</head>
	<body>
		<div>哈哈哈哈哈哈哈哈中午吃啥</div>
		
		
	</body>
</html>
<script type="text/javascript">
	var div=document.querySelector("div");
	//我们一般通过标签.style.属性值=值;进行赋值操作
	//那我们该如何取值呢
	var a=div.style.width;
	//这样取不可行
	//此操作正能对行间引用的css样式起作用 本质还是对象的.属性
	//对于外部引用的css样式或者head引用的css无法取出css样式的值
	
	console.log(a);
	//这是正确的去css样式值的方式
	//getComputedStyle(获取想要的标签样式)
	var obj=getComputedStyle(div);
	console.log(obj);
	console.log(obj.width);
	console.log(obj.height);
	console.log(obj["font-size"]);
	//取整操作
	var a="1782px";
	console.log(parseInt(a));
	var a1="哈哈哈1782px";
	console.log(parseInt(a1));
	var a2="1782哈哈哈px";
	console.log(parseInt(a2));
	var b=89.6767;
	var c=parseInt(b);
	console.log(c);
	//去小数操作
	a=10;
	console.log(parseFloat(a));
	a="241.31哈哈";
	console.log(parseFloat(a));
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/5029d7dbc63a4fba9f851681cb214717.png)
