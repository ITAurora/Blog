---
title: 前端HTML中定位后的居中问题
date: 2020-10-17 11:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/16.jpg
banner_img: ../articleImages/16.jpg
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
			.root{
				width: 600px;
				height: 600px;
				background-color: blue;
				margin: 0 auto;
				position: relative;
			}
			.one{
				width: 300px;
				height: 300px;
				background-color: black;
				position: absolute;
				left: 0;
				right: 0;
				top: 0;
				bottom: 0;
				margin: auto;
			}	
		</style>
	</head>
	<body>
		<div class="root">
			<div class="one"></div>
		</div>
	</body>
</html>

```
运行结果：
![](https://img-blog.csdnimg.cn/1c4846888a7a40a89bdba47e334c212a.png)
