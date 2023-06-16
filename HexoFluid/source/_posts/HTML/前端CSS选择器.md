---
title: 前端CSS的引用方式以及的CSS样式
date: 2020-02-25 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/4.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>CSS选择器</title>
		<style type="text/css">
			/*1.id选择器 唯一不可重复 搭配#使用*/
			#div1{
				background-color: #4169E1;
			}
			/*2.class类选择器 选中多个标签，搭配符号.使用*/
			.c1{
				background-color: #FF69B4;
				font-size: 30px;
			}
			/*3.标签选择器 选中文本中所有此类型的标签*/
			div{
				font-size: 33px !important;
			}
			/*------------复合型选择器-------------*/
			/*4.群组选择器*/
			/*不影响优先级 只是多选而已*/
			#div1,.c4{
				background-color: black;
			}
			/*5.后代选择器 空格*/
			/*box下的的所有a标签*/
			#box a{
				background-color: blue;
			}
			/*6.子代选择器  >*/
			/*只包括box下的一层a标签*/
			#box>a{
				background-color: red;
			}
			#box #one a{
				background-color: pink;
			}
			/*7.兄弟选择器*/
			.content li+li{
				background-color: red;
			}
			.content li+p{
				background-color: blue;
			}
			/*取消小黑点*/
			ul{
				list-style: none;
			}
		</style>
	</head>
	<body>
		<!--选择器是一种语法是为了精确的找到某一个或者几个标签！！
			优先级从高到底
			1.!important 只作用于一句话优先级最高(加在；里面)
			2.id #
			3.class .
			4.标签名 
			
		-->
		<!--div{div标签$}*6-->
		<!--id不能是单纯的数字，数字不能开头，例如2d，3d等-->
		<div id="div1">div标签1</div>
		<!--class类别-->
		<div id="div2" class="c1">div标签2</div>
		<div id="div3" class="c1">div标签3</div>
		<div id="div4">div标签4</div>
		<div id="div5">div标签5</div>
		<div id="div6">div标签6</div>
		<div id="div7" class="c2">div标签4</div>
		<div id="div8" class="c3">div标签5</div>
		<div id="div9" class="c4">div>标签6</div>
		<!--测试后代和子代选择器-->
		<a href="###">111111</a>
		<a href="###">222222</a>
		<div id="box">
			<a href="###">333333</a>
			<a href="###">444444</a>
			<div id="one">
				<a href="###">555555</a>
				<a href="###">666666</a>
			</div>
		</div>
		<!-------测试兄弟选择器--------->
		<!--ul>li{列表$}*8-->		
		<ul class="content">
			<li>列表1</li>
			<li>列表2</li>
			<li>列表3</li>
			<p>段落1</p>
			<p>段落2</p>
			<li>列表4</li>
			<li>列表5</li>
			<li>列表6</li>
			<p>段落3</p>
			<li>列表7</li>
			<p>段落4</p>
			<li>列表8</li>
		</ul>
	</body>
</html>

```
运行结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/8926aad864f242d897c7ce3ffc44c32a.png)
