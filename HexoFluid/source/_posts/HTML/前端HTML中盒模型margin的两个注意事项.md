---
title: 前端HTML中盒模型margin的两个注意事项
date: 2020-02-28 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/8.jpg
banner_img: ../articleImages/8.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

## 注意margin在块和行中的区别

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			#one{
				background:pink ;
				width: 300px;
				height: 300px;
				margin-bottom: 50px;
			}
			#two{
				background-color: deeppink;
				width: 300px;;
				height: 300px;
				margin-top: 100px;
			}
			#s1,#s2{
				background-color: yellow;
				margin-top: 50px;
				/*padding: 50px;*/
			}
			#s1{
				margin-right: 50px;
			}
			#s2{
				margin-left: 50px;
			}
		</style>
	</head>
	<body>
		<!--块元素   margin上下取最大值   左右取和-->
		<div id="one">
			遇事不决，可问春风。
		</div>
		<div id="two">
			春风不语，可随本心。
		</div>
		<!--行元素   margin上下无效    左右取和   padding正常 使用-->
		<span id="s1">
			行元素11111111
		</span>
		<span id="s2">
			行元素22222222
		</span>
	</body>
</html>

```
运行结果：
![](https://img-blog.csdnimg.cn/441b17cc074a41d991f9e8819bffb808.png)
## 用margin-top给第一个子代设置时属性会传给父级

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0px;
				padding: 0px;
			}
			#div1{
				background-color: blue;
			}
			#box{
				/*父子用padding兄弟用margin*/
				width: 1000px;
				height: 1000px;
				background-color: pink;
				/*方式一 给父类标签设置边框border 阻断top值传递*/
				/*border: 1px solid skyblue;*/
				/*方式二 给父级设置overflow:hidden;溢出部分隐藏*/
				/*overflow: hidden;*/
				/*最佳方案 以后父子间隔 给父级设置padding*/
				padding-top: 30px ;/*这样就不用再给第一个子标签设置marign值了*/
				
			}
			#one{
				/*margin—top属性会传给父类*/
				/*margin-top: 50px;*/
				width: 100px;
				height: 100px;
				background-color: red;
			}
			#two{
				width: 200px;
				height: 200px;
				background-color: orange;
			}
			#three{
				width: 300px;
				height: 300px;
				background-color: yellow;
			}
		</style>
	</head>
	<body>
		<div id="div1">哈哈哈</div>
		<div id="box">
			<div id="one">
				11111111
			</div>
			<div id="two">
				22222222
			</div>
			<div id="three">
				33333333
			</div>
		</div>
	</body>
</html>


```
运行结果：
![](https://img-blog.csdnimg.cn/cecac020900c45e0b124ad99720ee10e.png)


