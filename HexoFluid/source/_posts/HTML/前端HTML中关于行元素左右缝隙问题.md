---
title: 前端HTML中关于行元素左右缝隙问题
date: 2020-03-07 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/16.jpg
banner_img: ../articleImages/16.jpg
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
			div{
				background-color: black;
				font-size: 0;
			}
			span{
				background-color: blue;
				font-size: 16px;
			}
		</style>
	</head>
	<body>
		<div> 
		<span>111111111</span>
		<span>222222222</span>
		<span>333333333</span>
		<span>444444444</span>
		</div>
	</body>
</html>

<!--
	行元素缝隙是因为换行后的空格
	方案1:不换行  <span></span><span>
	方案2:浮动
	方案3:父级设置font-size:0; 再给子标签单独设置字号
	
	
-->
```

运行结果：
![](https://img-blog.csdnimg.cn/ab5840fc6755481cbb6cbacf57623b94.png)

