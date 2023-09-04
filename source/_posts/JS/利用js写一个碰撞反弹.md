---
title: 利用js写碰撞反弹方法
date: 2020-11-23 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/13.jpg
banner_img: ../articleImages/13.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

方法一:
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			#box{
				width: 800px;
				height: 400px;
				border: #2E8B57 3px solid;
				margin: 30px auto;
				position: relative;
			}
			#qiu{
				width: 50px;
				height: 50px;
				border-radius: 50%;
				background-color: gold;
				position: absolute;
				left: 0;
				top: 0;
			}
			
			
		</style>
	</head>
	<body>
		<div id="box">
			<div id="qiu"></div>
		</div>
	</body>
</html>
<script type="text/javascript">
	//记录当前的位置小球的位置
	var left = 0;
	var top1 = 0;
	//定义变量  用于设置小球left和top值的变化
	var x = 3; //水平方向  left
	var y = 2; //垂直方向  top
	
	
	//定义函数  用于小球移动
	function move(){
		left += x;
		top1 += y;
		
		//判断界限值!!! 水平方向  left值  
		if(left >= box.clientWidth - qiu.offsetWidth || left <= 0){
			x *= -1;
		}
		
		
		//判断top方向的临界值
		if(top1 >= box.clientHeight - qiu.offsetHeight || top1 <= 0){
			y *= -1;
		}
		
		//赋值给标签的属性
		qiu.style.left = left + "px";
		qiu.style.top = top1 + "px";
		
	}
	
	setInterval(move, 10);
	
	
	
	
</script>

```
方法二:

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
		<style type="text/css">
			#root{
				width: 600px;
				height: 400px;
				background-color: gray;
				margin: 100px auto;
				position: relative;
			}
			#qiu{
				width: 50px;
				height: 50px;
				border-radius: 50%;
				background-color: skyblue;
				position:absolute;
				transition: all linear .1s;
			}
		</style>
	</head>
	<body>
		<div id="root">
			<div id="qiu">
				
			</div>
		</div>
	</body>
</html>

<script type="text/javascript">
	var qiuleft=qiu.offsetLeft;
	var qiutop=qiu.offsetTop;
	var movex=true,movey=true;
	console.log(qiuleft);
	console.log(qiutop);
	var s1=setInterval(move,100);
	
	function move(){
		if(movex){
			qiuleft+=50;
			qiu.style.left=qiuleft+"px";
			if(qiuleft==600){
				movex=false;
			}
		}
		if(movex==false){
			qiuleft-=50;
			qiu.style.left=qiuleft+"px";
			if(qiuleft==0){
				movex=true;
			}
		}
		
		if(movey){
			qiutop+=50;
			qiu.style.top=qiutop+"px";
			if(qiutop==400){
				movey=false;
			}
		}
		if(movey==false){
			qiutop-=50;
			qiu.style.top=qiutop+"px";
			if(qiutop==0){
				movey=true;
			}
		}
		
	    }
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/01408d4057b44907a9872538a3e6bce4.png)
