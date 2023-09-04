---
title: 前端js中的className选择器
date: 2020-11-17 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/17.jpg
banner_img: ../articleImages/17.jpg
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
			ul{
				list-style: none;
				width: 500px;
				height: 40px;
				margin: 30px auto;
				display: flex;
				justify-content: space-around;
				cursor: pointer; 
			}
			.active{
				background-color: salmon;
				color: gold;
				font-size: 20px;
				border-bottom: aqua 5px solid;
			}
			li{
				transition: all .3s linear;
				border-radius: 20%;
			}
			.shadow{
				box-shadow: 0 0 10px 10px skyblue;
			}
		</style>
	</head>
	<body>
		<ul>
			<li class="active shadow">新闻</li>
			<li class="shadow">娱乐</li>
			<li class="shadow">国际</li>
			<li class="shadow">军事</li>
			<li class="shadow">汽车</li>
			<li class="shadow">生活</li>
		</ul>
	</body>
</html>
<script type="text/javascript">
	var liArray=document.getElementsByTagName("li");
	for (var i=0;i<liArray.length;i++) {
		liArray[i].onclick=function(){
			//设置class选择器
			this.className="active shadow";
			for (var j=0;j<liArray.length;j++){
				if(this!=liArray[j]){
					liArray[j].className="shadow";
				}
			}
		}
	}
</script>

```
运行结果：
![](https://img-blog.csdnimg.cn/67ea43adbcc642a2bb7c6f8be938e27f.png)
点击：
![](https://img-blog.csdnimg.cn/beed471faccb4714b3465f3bb6023aba.png)

