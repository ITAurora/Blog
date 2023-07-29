---
title: 前端HTML渐变色的使用
date: 2020-03-11 10:13:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/11.jpg
banner_img: ../articleImages/11.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>渐变</title>
		<style type="text/css">
			#one{
				width: 300px;
			    height: 200px;
				/*写法1*/
				/*background: -webkit-linear-gradient(pink,green);*/
				/*写法2*/
				background-image: -webkit-linear-gradient(left,yellow 60%,blue 80%);
			}
			#two{
				width: 300px;
				height: 300px;
				border: 5px solid red;
				margin: 0 auto;
				background: radial-gradient(closest-corner circle at center,yellow,red,blue);
			}
		</style>
	</head>
	<body>
		<div id="one">
			
		</div>
		<div id="two">
			
		</div>
		
	</body>
</html>
<!--1.线性渐变 常用 且好看
	默认渐变方形从上至下 默认每种渐变色所占区域相同
	2.径向渐变 圆形或者椭圆 不常用
	radial-gradient（半径 形状 at 圆心位置 颜色1百分比 颜色2百分比...）
	a.直接用px数值表示
	b.可以有以下形式表示
	最远边：father-side
	最近边：closest-side
	最远角：farther-corner
	最近角：closest-corner
	
	形状：
	圆形 circle 椭圆 ellipse
	
	圆心位置：
	默认的圆心在元素中心点上
	也可以设置px值 第一个值表示x轴方向 第二个表示y轴方向
	也可以用方位词表示像 left top right bottom
	渐变是对一个元素的背景设置也就是操作backgroung属性
	就是背景色渐变 渐变色至要有两种颜色参与
	渐变只是一个值 并不是一个新属性
-->
```
运行结果：
![](https://img-blog.csdnimg.cn/db60f392b69c4e3abee8f7820695ca7e.png)
