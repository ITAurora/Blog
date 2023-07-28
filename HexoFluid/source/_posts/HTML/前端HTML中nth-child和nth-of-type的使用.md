---
title: 前端HTML中nth-child和nth-of-type的使用
date: 2020-03-03 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/11.jpg
banner_img: ../articleImages/11.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
		<style type="text/css">
			li:nth-child(1){
				background-color: red;
			}
			li:nth-child(2){
				background-color: red;
			}
			/*不区分类型 统一从第一个标签记位置*/
			li:nth-child(2n-1){
				background-color: red;
			}
			/*
			 偶数 2n
			 奇数 2n-1
			 成倍查找 2n 3n 4n.....*/
			li:nth-of-type(3){
				background-color: blue;
			}
			li:nth-of-type(4){
				background-color: blue;
			}
		</style>
	</head>
	<body>
		<!--ul>li{列表$}*10-->
		<ul>
			<li>列表1</li>
			<p>段落1</p>
			<li>列表2</li>
			<li>列表3</li>
			<p>段落2</p>
			<li>列表4</li>
			<li>列表5</li>
			<li>列表6</li>
			<p>段落3</p>
			<li>列表7</li>
			<li>列表8</li>
			<li>列表9</li>
			<li>列表10</li>
			<p>段落4</p>
			<p>段落5</p>
			<p>段落6</p>
		</ul>
	</body>
</html>

```
![](https://img-blog.csdnimg.cn/08e6c4b2c5a3418b832c6516a8b1823a.png)
