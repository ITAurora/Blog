---
title: 前端利用js如何获取获取标签
date: 2020-11-03 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/9.jpg
banner_img: ../articleImages/9.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```js
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>在js中获取标签</title>
	</head>
	<body>
		<div id="one">这是div1</div>
		<p id="two">这是段落p</p>
		
		<div class="c1">哈哈</div>
		<div class="c1">呵呵</div>
		<h1 class="c1">嘿嘿</h1>
		
		<a href="###">京东</a>
		<div class="box">
			<a href="###">淘宝</a>
			<a href="###">天猫</a>
			<span >
				你说哈
			</span>
		</div>
		
	</body>
</html>

<script type="text/javascript">
	var d1 = document.getElementById("one");
	d1.style.backgroundColor = "red";
	d1.style.height = "100px";
	d1.style.opacity = 0.3;
	console.log(d1, typeof d1);
	//class选择器获取标签  ----------------
	var c1 = document.getElementsByClassName("c1");
	console.log(c1);
	console.log(typeof c1); //object
	//c1 根本就不是标签  而是装载标签的容器
	console.log(c1[0]);
	console.log(c1[2]);
	c1[0].style.backgroundColor = "green";
	//标签名获取
	var a1 = document.getElementsByTagName("a");
	console.log(a1);
	a1[0].style.backgroundColor = "yellow";
	//-----------------------------------
	//局部获取标签
	var box = document.getElementsByClassName("box")[0];
	var box_a = box.getElementsByTagName("a");
	var box_span = box.getElementsByTagName("span");
	console.log(box_a);
</script>
<!--
	1. id选择器不可重复  在js中只获取一个id标签
	2. className和tagName,获取的是装有标签的容器
	想获取具体的标签 容器[编号]  编号从0开始
	3. 获取id只能通过document
	4. 获取className或者TagName可以全局document也可以局部例如上述的box.get..ClassName()  box.get...TagName()
	记单词-----------------------
	document 指代当前上下文的文档对象!!!
	collection 容器
	HTMLElement 标签
	只有标签对象 才有资格.style
	这就是为什么要严格区分 标签对象  和   容器对象!!
	
	
	
-->

```
运行结果:
![](https://img-blog.csdnimg.cn/b8353bb85fab4d90888612c0bad61df9.png)

