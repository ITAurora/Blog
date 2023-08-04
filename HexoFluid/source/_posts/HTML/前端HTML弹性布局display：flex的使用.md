---
title: 前端HTML弹性布局display：flex的使用
date: 2020-03-15 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/3.jpg
banner_img: ../articleImages/3.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>弹性布局</title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			.box{
				width: 1100px;
				margin: 30px auto;
				border: solid 3px red;
				/*开启弹性盒子*/
				display: flex;
				/*是否换行
				 wrap 换行*/
				flex-wrap: wrap;
				/*-----设置主轴方向 默认是主轴横向的且从左至右*/
				 /*row-reverse 横向反方向 要有宽度
				 column 纵向正方向 要有高度*/
				/*flex-direction: row-reverse;*/
				/*flex-direction: column;*/
				/*设置主轴方向上的排布方式*/
				/*justify-content: space-between;*/
				justify-content: space-around;
				/*--------------设置侧轴方向的排布方式-----------*/
				 /*假设主轴是横向的话，侧轴就是纵向的； 这就需要父标签有高度
				 并且父级高度大于子标签内容高度！！！*/
				height: 450px;
				/*baseline 以文字为基线对齐
				 以个体的行为布局*/
				/*align-items: baseline;*/
				/*align-items: flex-start;*/
				/*整体的行布局*/
				align-content: space-around;
				
				
			}
			.box div{
				height: 200px;
				width: 200px;
				background-color: pink ;
				/*margin-bottom: 20px;*/
			}
			.box div:nth-child(2n){
				background-color: yellow;
			}
			.box div:nth-child(2){
				/*margin-top: 20px;*/
				/*padding: 20px;*/
			}
			/*--------------------------------------------------------*/
			/*弹性子元素属性*/
			/*调整某个弹性子盒子在几个位置显示*/
			.box div:nth-child(3){
				/*order: -1;*/
			}
			/*调整某个弹性子盒子在侧轴上的位置*/
			.box div:nth-child(2){
				/*align-self: flex-start;*/
				/*flex: 1;*/
			}
			/**/
			.box div:nth-child(4){
				
			}
		</style>
	</head>
	<body>
		<div class="box">
			<div>1</div>
			<div>2</div>
			<div>3</div>
			<div>4</div>
			<div>5</div>
			<div>6</div>
			<div>7</div>
			<div>8</div>
			<div>9</div>
			<div>10</div>
		</div>
	</body>
</html>
<!--
	小结：
	1.弹性属性给父级设置
	2.弹性盒子内部默认是单行布局
	3.一旦单行布局 字标签的宽度是无效的 会自动均分父级宽度
	4.子标签不设置高度，默认参考父级高度
-->

```
运行结果：
![](https://img-blog.csdnimg.cn/a396d0facd96429dbaa279140d2b822c.png)

