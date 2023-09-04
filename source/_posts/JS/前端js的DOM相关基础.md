---
title: 前端js的DOM相关基础
date: 2020-11-18 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/3.jpg
banner_img: ../articleImages/3.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
	</head>
	<body>
		
	</body>
</html>
<!--DOM： document object model
	文本对象模型 允许我们对html文档中的元素标签进行增删改查
	DOM树，当html文档加载完毕事 浏览器会根据我们书写的代码，创建一个树状结构
	DOM树，是由一个一个节点组成的
	结点的类型：
	1.元素节点 就是指各种标签
	2.声明节点  <!Document html>
	3.文本节点  就是文本内容 包括换行 回车等
	4.文档节点 document
	5.注释节点  就是注释
	
	节点之间的关系：
	1.父节点
	2.子节点
	3.兄弟节点
	
	关键区分：
	节点 Node
	元素/标签
-->
	<script type="text/javascript">
		//1.获取特殊节点类型
		//a.文档节点
		console.log(document);
		//b.html节点
		console.log(document.documentElement);
		//c.body节点
		console.log(document.body);
		//d.head节点
		console.log(document.head);
		//e.声明节点
		console.log(document.doctype);
		//练习:给body设置背景颜色
		//以后不需要给body标签设置任何id class等选择器
		document.body.style.backgroundColor="skyblue";
	</script>

```
运行结果:
![](https://img-blog.csdnimg.cn/611a2598330c4c1bb451011d761f64a9.png)
