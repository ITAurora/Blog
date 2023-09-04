---
title: 前端HTML移动端适配
date: 2020-10-27 12:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/2.jpg
banner_img: ../articleImages/2.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<!--移动端适配-->
		<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no" />
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			html{
				font-size: 16px
			}
			.one{
				width: 19.68rem;
				height: 300px;
				background-color: gold;
				position: absolute;
				left: 30px;
				right: 30px;
			}
			@media only screen and (min-width: 376px) {
				html{
				font-size: 17.98px
			}
			}
			@media only screen and (min-width: 820px) {
				html{
				font-size: 38.61px
			}
			}
			.two{
				width: 100px;
				height: 100px;
				background-color: yellow;
			}
		</style>
	</head>
	<body>
		<div class="one">
			<div class="two">
			
			</div>
		</div>
	</body>
</html>

```
运行结果：
窗口375的iPhone e上运行
![](https://img-blog.csdnimg.cn/1337d035b6934efba790386562925528.png)
窗口414的iphone xr上运行
![](https://img-blog.csdnimg.cn/e44fc8e2d37a4c4197ba16a761e03228.png)
在iPad air上运行
![](https://img-blog.csdnimg.cn/abf906e36d98470bb53969b59e81d6ac.png)

在不同设备上裕兴始终离左右边各30px