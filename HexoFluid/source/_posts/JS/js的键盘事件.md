---
title: js的键盘事件
date: 2020-11-30 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/8.jpg
banner_img: ../articleImages/8.jpg
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
			#one{
				width: 300px;
				height: 300px;
				background-color:skyblue ;
				position: absolute;
				
			}
		</style>
	</head>
	<body>
		<div id="one">
			
		</div>
	</body>
</html>
<script type="text/javascript">
	/*
	 * 键盘事件!!
	 * onkeydown
	 * onkeyup
	 * onkeypress
	 */
	window.onkeydown=function(){
		console.log(event);
		var l=one.offsetLeft;
		var t=one.offsetTop;
		console.log(event.keyCode,event.key)
		//通过属性keyCode就是按键的编码值 数字来控制
		switch(event.keyCode){
			case 37:
			console.log("左键");
			one.style.left=l-10+"px";
			break;
			case 38:
			console.log("上键");
			one.style.top=t-10+"px";
			break;
			case 39:
			console.log("右键");
			one.style.left=l+10+"px";
			break;
			case 40:
			console.log("下键");
			one.style.top=t+10+"px";
			break;
		    default:
		    break;
		}
	}
	//键盘弹起
	window.onkeyup=function(){
		console.log("键盘弹起");
	}
	//键盘按键一直按着才会执行
	window.onkeypress=function(){
		console.log("键盘持续按压");
	}
</script>
```
![](https://img-blog.csdnimg.cn/f9c97b1034574bd189be878e8054f940.png)
