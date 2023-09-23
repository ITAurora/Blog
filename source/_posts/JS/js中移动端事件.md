---
title: js中移动端事件
date: 2020-12-19 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/12.jpg
banner_img: ../articleImages/12.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no" />
		<title></title>
		<style type="text/css">
			
			*{
				margin: 0;
				padding: 0;
			}
			#one{
				width: 300px;
				height: 300px;
				background-color: slateblue;
			}
			
			
		</style>
	</head>
	<body>
		<div id="one"></div>
	</body>
</html>
<script type="text/javascript">
	var one = document.querySelector("#one");
	
//	one.ontouchstart = function(){
//		console.log("触摸开始");
//		console.log(event);
//		//支持多点触摸 就是同时放多个手指
//		//触摸点集合对象targetTouches
//		alert(event.targetTouches.length);
//	}
	
	one.addEventListener("touchmove", function(){
		console.log("触摸移动");
	});
	
	one.ontouchend = function(){
		console.log("触摸结束!!");
	}
	
	one.ontouchcancel = function(){
		console.log("触摸取消!!")
		//一般此方法的发生都是因为来电或者闹铃等一些事件打断了触摸!! 我们会在此事件中做一些数据存储等缓存任务!!!
	}
	
	
	
</script>
```
![](https://img-blog.csdnimg.cn/7aac5c1ee6c048d9aeb0611e07b029f5.png)
