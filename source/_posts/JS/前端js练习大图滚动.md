---
title: 前端js练习大图滚动
date: 2020-11-11 11:10:10
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
			
			*{
				margin: 0;
				padding: 0;
			}
			div{
				width: 520px;
				height: 350px;
				border: aquamarine 2px solid;
				margin: 20px auto;
				position: relative;
			}
			div img{
				position: absolute;
				left: 0;
				top: 0;
				opacity: 0;
			}
			div img:first-child{
				opacity: 1;
			}
			
			.btn{
				position: absolute;
				bottom: 0;
				width: 100%;
				height: 40px;
				border: none;
				text-align: center;
			}
			.btn p{
				display: inline-block;
				width: 60px;
				height: 40px;
				text-align: center;
				line-height: 40px;
				background-color: gold;
				font-weight: bold;
			}
		</style>
	</head>
	<body>
		<div>
			<img src="img/t1.png"/>
			<img src="img/t2.jpg"/>
			<img src="img/t3.jpg"/>
			<img src="img/t4.jpg"/>
			<img src="img/t5.jpg"/>
			<div class="btn">
			<p>图1</p>
			<p>图2</p>
			<p>图3</p>
			<p>图4</p>
			<p>图5</p>
			</div>
		</div>
	</body>
</html>
<script type="text/javascript">
	var pArray = document.getElementsByTagName("p");
	var imgArray = document.getElementsByTagName("img");
	
	//定义变量 来记录下标
	var index = 0;
	for(var i = 0; i < pArray.length; i++){
		pArray[i].onclick = function(){
			//隐藏当前正在显示的图片!!
			imgArray[index].style.opacity = 0;
			pArray[index].style.backgroundColor = "gold";

			//查找下标i
			for(var j = 0; j < pArray.length; j++){
				if(this == pArray[j]){
					index = j;
					break;
				}
			}
			//按钮he图片下标一致
			imgArray[index].style.opacity = 1;
		    pArray[index].style.backgroundColor = "orange";

		}
	}
	
</script>

```
运行结果:
![](https://img-blog.csdnimg.cn/2b35bedf73414aabbfe97285b2558c53.png)
点击:
![](https://img-blog.csdnimg.cn/a4761b70b4ee40d69944bbdd1769d5f5.png)

