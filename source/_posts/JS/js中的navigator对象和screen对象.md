---
title: js中的navigator对象和screen对象
date: 2020-11-27 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/4.jpg
banner_img: ../articleImages/4.jpg
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
	</body>
</html>
<script type="text/javascript">
	//navigator 用于检测浏览器内核操作系统的信息
	console.log(navigator);
	console.log(navigator.appName);
	console.log(navigator.appVersion);
	
	
	//screen 获取当前显示器的信息 尺寸 分辨率等
	console.log(screen);
	
	//availWidth 和 availHeight 浏览器的可用的最大宽高
	//width 和 height是显示器的宽高
	console.log(screen.availHeight);
	console.log(screen.height);
</script>

```
运行结果:
![](https://img-blog.csdnimg.cn/c3e8c6e6d66c4ec7ba55865de43ffbdd.png)
