---
title: 前端js标签的属性操作
date: 2020-11-19 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/7.jpg
banner_img: ../articleImages/7.jpg
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
		<img src="" alt=""/>
		<a href="###">京东</a>
		<div>测试标签</div>
	</body>
</html>
<script type="text/javascript">
	//1.如果是标签自带属性 可以直接访点语法访问
	//例如 img的src a的href input的value
	var img=document.querySelector("img");
	img.src="img/2.jpg";
	var a=document.querySelector("a");
	//2.如果是为了给标签做标记或者存储值我们可以自定义属性
	//object.属性 对象新增属性 点语法赋值/取值
	img.type="风景";//type就是自定义属性
	console.log(img);
	console.log(img.type);
	//标签增属性 可以看见 Attribute属性特征
	//方法赋值set/取值get
	img.setAttribute("aaa","hh");
	console.log(img.getAttribute("aaa"));
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/cbd6d0c8db0049f0a5ec10ae79d2d3fb.png)
