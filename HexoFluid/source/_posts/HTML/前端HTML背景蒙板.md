---
title: 前端HTML背景蒙板
date: 2020-03-11 10:12:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/10.jpg
banner_img: ../articleImages/10.jpg
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
			div{
				width: 600px;
				height: 600px;
				background: url(img/1.png);
				border: 3px solid gold;
				/*背景蒙板*/
				-webkit-mask-image: url(img/heart.png) ;
				/*蒙板尺寸*/
				-webkit-mask-size: 50px;
				/*蒙板平铺效果*/
				-webkit-mask-repeat:no-repeat;
				/*蒙板的位置*/
				-webkit-mask-position: center;
				/*也可以裁剪等 参考背景图片属性讲解即可 */
				/*综合写法 注意 背景图片属性也支持同时放置多张背景图片*/
				-webkit-mask:top url(img/heart.png),bottom url(img/nike.png);
				-webkit-mask-size:60px;
			}
		</style>
	</head>
	<body>
		<!--
			背景蒙板
			蒙板属性的兼容性比较差 只对webkit内核的浏览器有效果
			1.充当背景蒙板的图片格式必须是png
			2.设置成蒙板的图片 系统会把原本不透明的得部分变透明 
			把原本透明的
		-->
		<div class="">
			
		</div>
	</body>
</html>

```
运行结果：
![](https://img-blog.csdnimg.cn/66a165c46cbd4497b37004eef25b40c9.png)
