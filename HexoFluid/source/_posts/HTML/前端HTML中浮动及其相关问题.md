---
title: 前端HTML中浮动及其相关问题
date: 2020-02-28 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/10.jpg
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
	<link rel="stylesheet" type="text/css" href="css/浮动.css"/>
	<body>
		<!--浮动时平铺，盖不住字-->
		<!--clear解决兄弟造成的影响，overflow解决父子造成的影响-->
		<!--clear：both-->
		<div id="father">
			
		<div id="one">
			111111111
		</div>
		<div id="two">
			222222222
		</div>
		<div id="three">
			333333333
		</div>
		<div id="four">
			444444444
		</div>
		</div>
	</body>
</html>
<!--浮动之后，标签会脱离文档流，在网页上就无法再检测此标签
浮动曾不考虑标签独占一行，就是按照标签自身大小顺序排序，一行不够，自动换行
浮动的标签，会覆盖下面没有浮动的兄弟标签
-->

```
运行结果：
![](https://img-blog.csdnimg.cn/df2c6a8b012a478987aa682a5c81d3f1.png)

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			.father{
				width: 800px;
				background-color: palegreen;
				/*子标签全部浮动  没人撑起父标签高度   父标签检测不到子标签啦!!*/
				overflow: hidden;/*通过此属性可解决父子浮动问题*/
			}
			.child1{
				width: 100px;
				height: 100px;
				background-color: paleturquoise;
				float: left;
			}
			.child2{
				width: 200px;
				height: 200px;
				background-color: yellow;
				float: left;
			}
			.child3{
				width: 300px;
				height: 300px;
				background-color: pink;
				float: left;
			}
			
			h1{
				background-color: black;
				color: white;
			}
			
			
			
		</style>
	</head>
	<body>
		<div class="father">
			<div class="child1">111</div>
			<div class="child2">22</div>
			<div class="child3">333</div>
		</div>
		<!--做测试用!!!-->
		<h1>大标题</h1>
		
		
	</body>
</html>

```
运行结果：
![](https://img-blog.csdnimg.cn/976aa8b3c6a34a68a9702d1be7848169.png)
