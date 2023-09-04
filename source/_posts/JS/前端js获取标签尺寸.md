---
title: 前端js获取标签尺寸
date: 2020-11-20 10:10:10
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
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			.box{
				width: 300px;
				height: 300px;
				margin: 50px;
				background-color: skyblue;
				border: 5px solid gold;
				padding: 20px;
			}
			.one{
				width: 200px;
				height: 200px;
				background-color: gray;
			}
		</style>
	</head>
	<body>
		<div class="box">
			<div class="one">
				
			</div>
		</div>
		
	</body>
</html>
<script type="text/javascript">
	//1.获取标签
	var box =document.querySelector(".box");
	var one=box.firstElementChild;
	/*
	 2.和标签宽高尺寸相关的属性
	 内尺寸:width/height+ adding
	 clientWidth=width+左右padding
	 clientHeight=height+上下padding
	 
	 外尺寸:width/height+padding+border
	 offsetWidth=width+左右padding+左右border
	 offsetHeight=height+上下padding+上下border
	 
	 注意:内外尺寸就只差了一个border
	 
	 */
	console.log("内尺寸:",box.clientWidth,box.clientHeight);
	console.log("外尺寸:",box.offsetWidth,box.offsetHeight);
	
	/*
	 3.和标签距左距上的距离相关的属性
	 offsetLeft 是距离定位所参考的父级的左边的距离 (不包含border)
	 offsettop 是距离定位所参考的父级的上面的距离 (不包含border)
	 如果没有定位 就是默认到浏览器窗口左边或上面的距离
	 
	 */
	console.log(box.offsetLeft);
	console.log(box.offsetTop);
	console.log("测试one");
	console.log(one.offsetLeft);
	console.log(one.offsetTop);
	//输出所定位参考的父标签
	console.log(one.offsetParent);
	//------------------------------
	/*
	 4.不常用的 了解即可
	 clientLeft: 获取标签做边框的宽度
	 clienttop: 获取上边框的宽度
	 */
	console.log("box:",box.clientLeft,box.clientTop);
	console.log("one:",one.clientLeft,one.clientTop);
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/b2b7b03d55ce4437bf5799e1bb6e58d7.png)
