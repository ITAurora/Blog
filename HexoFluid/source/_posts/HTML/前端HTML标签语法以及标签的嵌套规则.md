---
title: 前端HTML标签语法以及标签的嵌套规则
date: 2020-02-23 10:10:10
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
		<title></title>
	</head>
	<body>
		<!--标签*n 生成n个标签
			标签1+标签2 生成两个为兄弟关系的标签
			标签1>标签2 生成两个为父子关系的标签
			标签{文本} {是设置文本}
			父标签>子标签* 父标签中多个子标签
			$ 自增 从一开始
			先执行需要加（）进行优先级
		-->
	</body>
</html>
```


```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<!--块元素嵌套行元素 很常见而且常用-->
		<div>
			<a href="###">羽绒服</a>
			<a href="###">微淘</a>
		</div>
		<a href="###">测试</a>
		<!--ul li也可以嵌套其他块元素和行元素-->
		<ul>
			<li>
				<span>123456</span>
				<p>段落</p>
			</li>
		</ul>
		<!--a标签可以嵌套其他块元素-->
		<a href="###">
			<div>
				<img width="300" height="300" src="img/3.jpg"/>
				<span>123456</span>
			</div>
		</a>
		
		<!--重点-->
		<!--p标签段落标签 用于设置文本 不允许嵌套任何块元素-->
	<div>
		<p>这是一段文字</p>
	</div>
	<div>
		<div>这是一个div块</div>
	</div>
	<div>
		<ul>
			<li>列表</li>
		</ul>
	</div>
	</body>
</html>

```
运行结果:
![在这里插入图片描述](https://img-blog.csdnimg.cn/bf7780f4aee844a5b94bd122c8dc4dfd.png)

