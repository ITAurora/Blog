---
title: 前端HTML中display属性的使用
date: 2020-03-04 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/13.jpg
banner_img: ../articleImages/13.jpg
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
			div,span{
				background-color: pink;
				border: 1px solid red;
			}
			div{
				width: 100px;
				height: 100px;
				/*display: inline;*/
			}
			span{
				display: block;
			}
			/*多行文本上下居中*/
			#div1{
				
				display: table;
				width: 300px;
				height: 300px;
				background-color: #0000FF;
			}
			#div1 p{
				display: table-cell;
				vertical-align: middle;
			}
			/*多行文本上下居中对齐*/
			#div2{
				width: 400px;
				background-color: pink;
				padding: 20px 0;
			}
		</style>
	</head>
	<body>
		<div id="d1">
		这是一个div111111
		</div>
		<div id="d2">
			这是一个div22222222
		</div>
		<span id="s1">
			这是一个span1111111
		</span>
		<span id="s2">
			这是一个span2222222
		</span>
		<div id="div1">
			<p>带p标签的div带p标签的div带p标签的div带p标签的div带p标签的div</p>
		</div>
		<div id="div2">
			<p>不带p标签的div不带p标签的div不带p标签的div不带p标签的div</p>
		</div>
	</body>
</html>
<!--
	display属性
	block 转为
	
-->
```
![](https://img-blog.csdnimg.cn/9a7fbd6bccf440a1b76e694197cb8958.png)