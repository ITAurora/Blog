---
title: 前端js中的onclick点击事件
date: 2020-11-04 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/12.jpg
banner_img: ../articleImages/12.jpg
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
			div{
				width: 100px;
				height: 50px;
				background-color: skyblue;
				margin: 40px;
			}
		</style>
	</head>
	<body>
		<!--设置点击事件  方式1-->
		<div onclick="aaa()">点击这里</div>
		<!--方式2  更常用-->
		<div>看我看我</div>
	</body>
</html>
<script type="text/javascript">
	//对应实现点击事件的方法
	function aaa(){
		console.log("哈哈哈");
		var body = document.getElementsByTagName("body")[0];
		body.style.backgroundColor = "yellow";
	}
	//--------
	//方式2
	var two_div = document.getElementsByTagName("div")[1];
	//绑定点击事件  一旦单击div  立马执行function
	two_div.onclick = function(){
		console.log("你好!");
	}
	
	
</script>

<script type="text/javascript">
	
	
</script>

```
运行结果:
![](https://img-blog.csdnimg.cn/717f6bfc58b1443cb7fea382c8a10638.png)
点击事件触发1:
![](https://img-blog.csdnimg.cn/04045b73ad5242a683d97e2cba0c5c61.png)
点击事件触发2:注意看控制台
![](https://img-blog.csdnimg.cn/c79e43a239c2483598bfbcf4d8e638d5.png)
点击:
![](https://img-blog.csdnimg.cn/a892ed3e893b4ad992abdba147e55ed0.png)



