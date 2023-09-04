---
title: js的滚轮事件
date: 2020-11-30 12:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/9.jpg
banner_img: ../articleImages/9.jpg
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
		
	</body>
</html>
<script type="text/javascript">
	//滚轮事属于鼠标事件 只是滚轮兼容性不一样
	//滚轮事件直接加给文档
	document.onmousewheel=function(){
		//注意 wheelDelta不是date
		//此方法不兼容火狐浏览器
		console.log(event.wheelDelta);
		if(event.wheelDelta>0){
			console.log("向上滚动");
		}
		if(event.wheelDelta<0){
			console.log("向下滚动");
		}
	}
	//如何兼容火狐浏览器
	//利用
	document.addEventListener("DOMMouseScroll",function(e){
		//火狐浏览器 事件在参数部分就是e
		console.log("火狐滚轮事件");
		//滚动值
		console.log(e.detail);
		if(e.detail>0){
			console.log("火狐滚轮事件向下滚动");
		}else{
			console.log("火狐滚轮事件向上滚动");
		}//正负值与其他浏览器相反
		//尽量以正负值判断上下滚轮
	});
</script>
```
![](https://img-blog.csdnimg.cn/9a5778dc436d423599980d15fded2585.png)
