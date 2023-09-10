---
title: js的元素拖拽属性
date: 2020-12-06 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/14.jpg
banner_img: ../articleImages/14.jpg
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
			*{
				margin: 0;
				padding: 0;
			}
			#one{
				width: 300px;
				height: 300px;
				background-color: gold;
				position: absolute;
			}
		</style>
	</head>
	<body>
		<div id="one"></div>
	</body>
</html>
<script type="text/javascript">
	//元素拖拽 就是鼠标去哪里要通过你的event.clientx取值
	//标签跟着去哪里要给其赋值
	//这是方式1 
//	document.onmousemove=function(){
//		console.log(event.clientX,event.clientY);
//		one.style.left=event.clientX+"px";
//		one.style.top=event.clientY+"px";
//	}
	//这是方式2 比较好看
	//我是希望鼠标点击one标签进行拖拽 松手就停
	//而且移动过程中 鼠标和one是相对静止的
	one.onmousedown=function(){
		//鼠标点在了one标签的哪个位置
		var left1=event.offsetX;
		var top1=event.offsetY;
		document.onmousemove=function(){
			one.style.left=event.clientX-left1+"px";
			one.style.top=event.clientY-top1+"px";
		}
	}
	//鼠标弹起 取消移动
	one.onmouseup=function(){
		document.onmousemove=null;
	}
	
</script>
```
![](https://img-blog.csdnimg.cn/7805316f422d46b78d328ae52edd7dac.png)
