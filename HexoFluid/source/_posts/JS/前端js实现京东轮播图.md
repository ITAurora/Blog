---
title: 前端js实现京东轮播图
date: 2020-11-13 11:10:10
tags:
  - JS
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
		<meta charset="utf-8" />
		<title>京东轮播图</title>
		<link rel="stylesheet" type="text/css" href="css/jingd.css"/>
	</head>
	
	<body>
		<div class="root">
			<!--轮播图-->
			<div class="lunbo">
				<img src="img/t1.png"/>
				<img src="img/t2.jpg"/>
				<img src="img/t3.jpg"/>
				<img src="img/t4.jpg"/>
				<img src="img/t5.jpg"/>
			</div>
			<!--左右切换按钮-->
			<div class="btn">
				<div class="left-btn"></div>
				<div class="right-btn"></div>
			</div>
			<!--圆点指示器-->
			<ul class="dots">
				<li></li>
				<li></li>
				<li></li>
				<li></li>
				<li></li>
			</ul>
		</div>
	</body>
</html>
<script src="js/jd.js" type="text/javascript" charset="utf-8"></script>

```
运行结果:
会自动播放
鼠标触及停止
点一次播放一次
![](https://img-blog.csdnimg.cn/045d85a4cb0743049d29c1ed23840aaf.png)
