---
title: 前端HTML中vm和vh单位的使用
date: 2020-10-27 11:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/1.jpg
banner_img: ../articleImages/1.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no" />
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			.one{
				width: 300px;
				height: 300px;
				background-color: pink;
				font-size: 5vw;
			}
			/*vw 参考窗口的宽度 1vw就是1%
			 */
			.two{
				width: 30vw;
				height: 30vh;
				background-color: red;
			}
		</style>
	</head>
	<body>
		<div class="one">
			123456789
			<div class="two">
				987654321
			</div>
		</div>
	</body>
</html>

```
运行结果：
此时是最大窗口
![](https://img-blog.csdnimg.cn/4e3769ea81b94dcca3ca23fef9b9e1d1.png)
缩小窗口
![](https://img-blog.csdnimg.cn/5df9c17d257a41d3936cc90946c09c15.png)
继续缩小
![](https://img-blog.csdnimg.cn/bca4d8de745c4e97a436c3554d0c486e.png)
