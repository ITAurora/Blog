---
title: js绑定事件以及事件冒泡
date: 2020-12-05 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/13.jpg
banner_img: ../articleImages/13.jpg
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
			img{
				width: 600px;
				height: 600px;
			}
			#one{
				overflow: hidden;
				width: 300px;
				height: 300px;
			}
		</style>
	</head>
	<body>
		<div id="one">
			<img src="img/5.jpg"/>
		</div>
		<button id="btn">点击</button>
	</body>
</html>
<script type="text/javascript">
	//标签的内容滚动 这个属于DOM操作
	//使用场景 :放大镜
	//scrollLeft  scrollTop 即可赋值
	//
	var l=20;
	btn.onclick=function(){
		one.scrollLeft=l;//点击向左移动20
		one.scrollTop=l;//点击向上移动20
		console.log(one.scrollLeft);
		console.log(one.scrollTop);
		l+=20;
	}
</script>
```
![=](https://img-blog.csdnimg.cn/6a1a387b3f554a77b480140477c23084.png)
