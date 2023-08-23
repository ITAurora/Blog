---
title: 前端js通过关系获取节点
date: 2020-11-18 12:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/5.jpg
banner_img: ../articleImages/5.jpg
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
		测试测试测试
		<!--这是一个注释-->
		<div id="one">哈哈哈</div>
		<p>这是一个段落标签</p><span>这是一个span标签</span><div id="box">
			<span>娃娃鱼</span>
			<span>托儿所</span>
		</div>
		<!--ul>li{列表$}*3-->
		<ul>
			<li>列表1</li>
			<li>列表2</li>
			<li>列表3</li>
		</ul>
	</body>
</html>
<script type="text/javascript">
	//获取节点
	//1.childNodes 获取的是子节点 会得到一个节点数组
	var a1=document.body.childNodes;
	console.log(a1);
	//2.parentNode 获取到某个节点的父节点(节点的父节点只有一个)
	var a2= document.querySelector("#box").parentNode;
	console.log(a2);
	//3.firstChild 获取某个节点中的第一个子节点
	console.log(document.body.firstChild);
	//4.lastChild 获取某个节点中的最后一个子节点
	console.log(document.body.lastChild);
	//5.获取某个节点的上一个兄弟节点
	console.log(document.querySelector("span").previousSibling);
	//6.获取某个节点的下一个兄弟节点
	console.log(document.querySelector("span").nextSibling);
	//-------------仅仅获取标签节点 重点使用最多
	//1.获取某个节点的所有 元素子节点
	console.log(document.body.children);
	//2.获取某个节点的 父元素节点
	console.log(document.querySelector("div").parentElement);
	//3.获取某个节点中的 第一个元素节点
	console.log(document.querySelector("ul").firstElementChild);
	//4.获取box中的最后一个元素节点
	var box =document.querySelector("#box");
	console.log(box.lastElementChild);
	//5.获取box标签的上一个兄弟元素节点
	console.log(box.previousElementSibling);
	//6.获取box标签的下一个兄弟元素节点
	console.log(box.nextElementSibling);
	//7.获取某个节点中 子元素节点的个数(子标签个数)
	console.log(box.childElementCount);
	
	
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/dcfd683be07d4ffa8ceb070f1372035d.png)
