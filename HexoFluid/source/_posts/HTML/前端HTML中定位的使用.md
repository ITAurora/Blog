---
title: 前端HTML中定位的使用
date: 2020-03-05 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/14.jpg
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
			body{
				height: 2000px;
			}
			*{
				padding: 0;
				margin: 0;
			}
			#d1{
				width: 200px;
				height: 200px;
				background-color: pink;
				position: static;
				margin: 20px;
				left: 100px;
				top: 100px;
			}
			#d2{
				height: 300px;
				width: 300px;
				background-color: gray;
				margin: 20px;
			}
			/*测试相对定位*/
			#d3{
				background-color: blue;
				width: 100px;
				height: 100px;
				margin-left: 50px;
				margin-top: 100px;
				position: relative;
				left: 20px;
				top: 20px;
				
			}
			/*测试绝对定位*/
			#d4{
				width: 150px;
				height: 150px;
				background-color: pink;
				position: absolute;
				top: 20px;
				left: 20px;
			}
			/*测试绝对定位的父子位置约束*/
			#father{
				width: 300px;
				height: 300px;
				background-color: pink;
				margin: 50px auto;
				padding: 20px;
				position: relative;
			}
			#son{
				width: 200px;
				height: 200px;
				background-color: gold;
				position: absolute;
				left: 10px;
			}
			#sonsong{
				width: 100px;
				height: 100px;
				background-color: orange;
				position: absolute;
				left: 10px;
			}
			ul{
				list-style: none;
			}
			li{
				position: absolute;
				top: 20px;
				left: 500px;
			}
			li:first-child{
				width: 100px;
				height: 100px;
				background-color: red;
				z-index: 3;
				
			}
			li:nth-child(2){
				width: 200px;
				height: 200px;
				background-color: green;
				z-index: 2;
			}
			li:last-child{
				width: 300px;
				height: 300px;
				background-color: blue;
				z-index: 1;
			}
			#fixed{
				width: 100%;
				height: 30px;
				background-color: black;
				position: fixed;
				left: 0;
				top: 0;
			}
		</style>
	</head>
	<body>
		<!--1.测试静态定位-->
		<div id="d1">测试静态定位1</div>
		<div id="d2">测试静态定位2</div>
		<!--2.测试相当定位-->
		<div id="d3">测试相对定位3</div>
		<h1>标题标签</h1>
		<!--测试绝对定位-->
		<div id="d4">测试绝对定位4</div>
		<h1>标题标签</h1>
		<!--测试父子-->
		<div id="father">
			<div id="son">
				<div id="sonsong">
					123
				</div>
			</div>
		</div>
		<ul>
			<li>绝对定位</li>
			<li>兄弟2</li>
			<li>兄弟3</li>
		</ul>
		<!--测试固定定位-->
		<div id="fixed">
			123
		</div>
	</body>
</html>
<!--
	定位 position 定位效果不会影响盒模型
	1.静态定位 static
	是默认值 无任何效果 可忽略
	2.相对定位 relative
	不会脱离文档流 会为标签保留原始位置
	相对自身定位位置会发生移动
	3.绝对定位 absolute
	会脱离文档流 不会保留其位置
	默认相对浏览器窗口进行位置移动，但如果其有父标签且父标签还设置
非静态定位的其他定位方式 就参考父级进行位置移动
	如果多个相邻的兄弟元素都进行了绝对定位 那么越晚设置定位的 层级越
靠上
	调整层级的属性 z-index：数值；0为默认值 值越大层级越靠上
	4.固定定位 fixed
	会脱离文档流，所以不会为其保留位置，不会随着网页滚动而滚动 是固
定在一个位置上
	相对浏览器窗口进行位置移动!
	定位属性 需要搭配四个方向属性使用 left top right bottom
-->

```
运行结果：
![](https://img-blog.csdnimg.cn/09657ee717ae4e2482f26c2c3f487d8f.png)

