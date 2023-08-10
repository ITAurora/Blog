---
title: 前端HTML中的hover选择器
date: 2020-10-12 12:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/6.jpg
banner_img: ../articleImages/6.jpg
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
			.one{
				background-color: tomato;
				width: 300px;
				height: 300px;
				line-height:300px;
			}
			/*：hover 用来捕捉鼠标进入标签状态
			 注意： 冒号：前后不准加空格*/
			.one:hover{
				background-color: pink;
				width: 200px;
				height: 200px;
				line-height:200px;
			}
		</style>
	</head>
	<body>
	<div style="font-size: 50px; text-align: center;" class="one">
		一
		<hr />
	</div>
	</body>
</html>

```
运行结果：
此时鼠标不在橙色区域上
![](https://img-blog.csdnimg.cn/319371073d7648f99b81ec894abe4d06.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBASVQtQXVyb3Jh,size_20,color_FFFFFF,t_70,g_se,x_16)
把鼠标放在橙色区域上
![](https://img-blog.csdnimg.cn/2df902d6e4a14ae3a0a3e524ac00b63d.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBASVQtQXVyb3Jh,size_20,color_FFFFFF,t_70,g_se,x_16)
