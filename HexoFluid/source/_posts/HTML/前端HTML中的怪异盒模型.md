---
title: 前端HTML中的怪异盒模型
date: 2020-03-10 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/5.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
		<style type="text/css">
			.box{
				width:300px;
				height: 300px;
				padding: 20px;
				border: 5px solid red;
				margin: 20px;
				background: #008000;
				/*修改盒模型样式*/
				/*border-box属性值   怪异盒模型样式
				 padding和border会向内占用宽高尺寸
				*/
				/*默认值是 content-box; 标准盒模型*/
				box-sizing: border-box;
			}
		</style>
	</head>
	<body>
		<div class="box">
			
		</div>
	</body>
</html>

```
未加box-sizing: border-box;属性时的
运行结果：仔细看右边盒模型结构
![](https://img-blog.csdnimg.cn/036660a46d474502bacc5fb1e692d4cf.png)
加上box-sizing: border-box;怪异盒模型属性时的
运行结果：仔细看右边怪异盒模型结构

![](https://img-blog.csdnimg.cn/5bcddfd053884782a921bd343411af95.png)
