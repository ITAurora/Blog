---
title: js中event对象以及其相关属性
date: 2020-12-05 10:10:10
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
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			body{
				height: 3000px;
			}
			#one{
				width: 300px;
				height: 300px;
				background-color: sandybrown;
				margin: 40px;
			}
			
			
		</style>
	</head>
	<body>
		<div id="one">
			
		</div>
	</body>
</html>
<script type="text/javascript">
	//但凡是..x  ..y 说的都是鼠标的位置!!只有位置才是一点,是一个点才有x y值!!
	
	//以后但凡是...width  ...height ...left  ..top 这些都是说标签的值!!
	//one 也就是事件源标签  事件发生的源头标签
	one.onclick = function(){
		//是鼠标距离浏览器窗口左侧 和  上边的距离!! clientX  clientY
//		console.log(event.clientX, event.clientY);
		
		//是鼠标距离被点击的标签的左侧和上侧距离     offsetX  offsetY
//		console.log(event.offsetX, event.offsetY);


        //是鼠标距离窗口中内容区域的左侧he上面的距离  哪怕发生向上滚动 也能检测到距离页面内容顶部的距离!pageX  pageY
//      console.log(event.pageX, event.pageY);
        
        
        //screenX  screenY screen就是设备屏幕的意思
        //所以是鼠标距离屏幕左侧和上面的距离 一般很少用!!
//	   console.log(event.screenX, event.screenY);
	}
</script>

```
![](https://img-blog.csdnimg.cn/d357b31be97847e291fbdc687cff6a9b.png)
