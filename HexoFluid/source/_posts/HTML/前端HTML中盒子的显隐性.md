---
title: 前端HTML中盒子的显隐性
date: 2020-03-04 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/12.jpg
banner_img: ../articleImages/12.jpg
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
			.one{
				width: 600px;
				height: 600px;
				background-color: pink;
				/*真正控制显性和隐性的属性*/
				/*hidden隐藏  visible显示*/
				/*visibility: hidden;*/
				/*透明度属性 间接认为i可以控制显示和隐藏
				 0 完全透明 相当于隐藏
				 1 不透明 相当于显示*/
				/*opacity: 0;*/
				/*display 转换转化 none转为空*/
				display: none;
			}
			.one:hover{
				/*visibility: visible;*/
				/*opacity: 1;*/
				display: block;
				background-color: blue;
			}
		</style>
	</head>
	<body>
		<div class="one">
			
		</div>
		<h1>测试显隐性</h1>
	</body>
</html>
<!--
	1.显隐属性 visibility
	保留位置 但是触摸不到标签
	隐藏：hidden 显示：visible
	
	2.透明度属性 opacity
	保留位置 标签一直都在 只是透明化了
	隐藏：opacity：0； 显示：opacity：1；
	可以设置动画效果
	
	3.标签转换特性属性 display
	不保留位置 相当于标签注解转化为空 所以位置也不会保留
	隐藏：display：none； 显示：display：block；
-->
```