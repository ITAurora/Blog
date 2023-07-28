---
title: 前端HTML盒模型
date: 2020-02-28 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/7.jpg
banner_img: ../articleImages/7.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>盒模型</title>
		<style type="text/css">
			/*---*号是通配符，匹配所有标签
			 可用来初始化操作
			 ------*/
			*{
				/*外边距和内填充归零*/
				margin: 0;
				padding: 0;
			}
			#one{
				background-color: pink;
				text-align: center;
				width: 300px;
				height: 300px;
				/*padding 内填充 注意：内填充颜色同背景且不可更改*/
				/*上下左右*/
				padding: 20px;
				/*上下 左右*/
				/*padding: 20px 30px;*/
				/*上 左右 下*/
				/*padding: 20px 30px 4px;*/
				/*上 下 左 右*/
				/*padding: 20px 30px 40px 50px;*/
				/*也可单指*/
				/*padding-left: 30px;*/
				/*--------------------------------------------------*/
				/*边框*/
				border-color: red;
				border-width: 20px;
				/*边框风格  solid实线最常用   dotted圆点型虚线     dashed矩形虚线       groove立体虚线*/
				border-style: dashed;
				/*复合写法   比较常用 */
				border: 20px dashed blue;
				/*定向选择一个方向*/
				border-left: green 20px solid;
				/*---------------------------------------------------*/
				/*边框圆角
				 单值  切四个角全
				 两个值 切两个对角线 即左上右下和右上左下
				 三个值 对角线 左上   右上左下  右下
				 四个值 顺时针 从左上开始
				 */
				border-radius: 150px 50% 0 0;
				/*按照位置切圆角*/
				/*border-bottom-left-radius: 50%;*/
			}
		</style>
	</head>
	<body>
		<div id="one">
			遇事不决，可问春风。
		</div>
	</body>
</html>

```
运行结果：
![](https://img-blog.csdnimg.cn/5fb9451f01bb46478ca1ecd5798ba583.png)
