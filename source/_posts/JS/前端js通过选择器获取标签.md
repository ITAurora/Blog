---
title: 前端js通过选择器获取标签
date: 2020-11-18 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/4.jpg
banner_img: ../articleImages/4.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		
		<div id="one"></div>
		<div class="c1"></div>
		<h1 class="c1"></h1>
		<a href="###">哈哈哈哈</a>
		<div class="box">
			<a href="###">京东</a>
			<a href="###">淘宝</a>
		</div>
	</body>
</html>
<script type="text/javascript">
	//通过css选择器获取标签
	//1.获取所有符合条件的标签,所以返回值是数组
	//标签选择器
	var divArray=document.querySelectorAll("div");
	console.log(divArray);
	//class选择器
	var c1Array=document.querySelectorAll(".c1");
	console.log(c1Array);
	//后代选择器
	var aArray=document.querySelectorAll(".box a:first-child");
	console.log(aArray);
	//2.只获取符合条件的第一个标签
	//所以返回值就是具体的标签对象
	var a=document.querySelector(".box a");
	console.log(a);
	var one=document.querySelector("#one");
	console.log(one);
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/fa3b6dc08c8c494a8637174d41209a28.png)
