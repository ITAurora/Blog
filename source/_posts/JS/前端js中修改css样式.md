---
title: 前端js中修改css样式
date: 2020-11-03 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/10.jpg
banner_img: ../articleImages/10.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```js
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			#one{
				width: 200px;
				height: 200px;
				background-color: gold;
			}
		</style>
	</head>
	<body>
		<div id="one">测试测试</div>
	</body>
</html>

<script type="text/javascript">
	// top 不能设置为变量名,它是系统保留字!!
	var div = document.getElementsByTagName("div")[0];
	div.style.width = "400px";
	div.style.position = "absolute";
	div.style.left = "100px";
	div.style.top = "100px";
	div.style.zIndex = 2;
	
	
	//修改css样式
	/*
	 1.只有纯数字,可以不需要设置"" 例如z-index:10; opacity:0.4;
	 2.例如宽高,left,right等   "100px"; "20px";  "10%"; "2em"
	 3.在js中修改css样式,必须通过关键词style
	 标签对象.style.样式属性 = 值;
	 4.样式属性在js中,都是驼峰命名法 
	 例如:backgroundColor  zIndex  left  fontSize
	 css中是font-size 使用-来连接多个单词
	 */
	
	
	
</script>

```
运行结果:
![](https://img-blog.csdnimg.cn/fa1003ef92384198b440f921443c0528.png)


