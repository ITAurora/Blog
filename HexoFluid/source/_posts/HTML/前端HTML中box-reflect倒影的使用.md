---
title: 前端HTML中box-reflect倒影的使用
date: 2020-03-15 12:10:10
tags:
  - HTML
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
		<title>倒影</title>
		<style type="text/css">
			/*倒影只是一个影像 不占据空间*/
			/*1.倒影的位置
			 left 在实物的左侧 right 在右侧
			 above 在标签上方 below 在标签下方
			 2.距离实物的距离 单位px*/
			.bottom{
			/*盒子不写宽时默认与父级同宽高度由内容撑起*/
				width: 600px;
				/*普通写法*/
				/*-webkit-box-reflect: below 10px;*/
				/*越来越越透明的写法 就是渐变倒影*/
				-webkit-box-reflect:below -300px
				-webkit-linear-gradient(/*left*/top,transparent,red);
			}
			.bottom img{
				width: 600px;
			}
		</style>
	</head>
	<body>
		<span>下倒影</span>
		<div class="bottom">
			<img src="img/heart.png"/>
		</div>
	</body>
</html>

```
运行结果：
![](https://img-blog.csdnimg.cn/14cbc279349f4c79b50ad3b9a66701a8.png)



