---
title: 前端HTML弹窗的实现
date: 2020-03-09 10:11:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/4.jpg
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
			#i1{
				width: 180px;
				height: 30px;
				padding-left: 10px;
				/*去掉默认带的外线框*/
				outline: none;
				/*重新设置边框*/
				border:1px solid lightgray;
				border-radius: 6px;
			}
			/*焦点选择器   只有标签获取焦点才会执行*/
			#i1:focus{
				border-color: skyblue;
			}	
			
			.one{
				width: 300px;
				height: 120px;
				background-color: skyblue;
				display: none;
			}
			
			#i1:focus+.one{
				display: block;
			}
		</style>
	</head>
	<body>
		
		<input type="text" id="i1" placeholder="请输入账号"/>
		<div class="one">
			这是弹框
		</div>
		<h1>大标题  测试</h1>
	</body>
</html>

```
运行结果：
![](https://img-blog.csdnimg.cn/40914bcedf7d40ebb7d28125acb1d8fa.png)
![](https://img-blog.csdnimg.cn/347dd5a008d4407c88cab248c7447f0c.png)

