---
title: js之碰撞检测
date: 2020-12-07 12:10:10
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
				/*通过css方式  关闭标签的用户选中效果!!!*/
				/*-webkit-user-select: none;
				-moz-user-select: none;
				-ms-user-select: none;*/
			}
			div{
				width: 200px;
				height: 200px;
				font-size: 50px;
				line-height: 200px;
				text-align: center;
			}
			#one{
				background-color: pink;
				position: absolute;
				left: 0;
				top: 0;
			}
			#two{
				background-color: skyblue;
				position: absolute;
				left: 0;
				top:0;
				right: 0;
				bottom: 0;
				margin: auto;
			}
		</style>
	</head>
	<body>
		<!--重点!! 不难!!-->
		<div id="one">1</div>
		<div id="two">2</div>
	</body>
</html>
<script type="text/javascript">
	//给one添加拖拽效果
	one.onmousedown = function(){
		//通过js方式   取消事件默认样式
		event.preventDefault();
		
		var l = event.clientX - this.offsetLeft;//鼠标距离点击的标签的左边距离
		var t = event.offsetY;//offsetY 是鼠标距离点击的标签的上面的距离
	window.onmousemove = function(){
		one.style.left = event.clientX - l + "px";
		one.style.top = event.clientY - t + "px";
		
		
		//在move中 不停的判断 是否两个标签碰撞
		if (crash(one, two)) {
			two.style.backgroundColor = "green";
		}else{
			two.style.backgroundColor = "skyblue";
		}
	}
	}
	//鼠标从one上抬起来
	one.onmouseup = function(){
		window.onmousemove = null;
	}
	
	//---封装函数    碰撞检测
	//通过四个方向上的临界值来判断是否发生了碰撞
	function crash(div1, div2){
		var xLeft = div2.offsetLeft - div1.offsetWidth;
		var xRight = div2.offsetLeft + div2.offsetWidth;
		
		var yTop = div2.offsetTop - div1.offsetHeight;
		var yBottom = div2.offsetTop + div2.offsetHeight;
		//只要div1 在这4个临界值内 那么就说明发生了碰撞
		 if(div1.offsetLeft >= xLeft && div1.offsetLeft <= xRight && div1.offsetTop >= yTop && div1.offsetTop <= yBottom){
		 	return true;
		 }else{
		 	return false;
		 }
		
	}
	
</script>
```
![](https://img-blog.csdnimg.cn/a5450f3fe1104a05b198062d0163995d.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/e0e6f1ae8bb24cc88a08b4729478006c.png)


