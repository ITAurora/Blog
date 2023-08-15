---
title: 前端js中function构造匿名函数
date: 2020-11-10 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/6.jpg
banner_img: ../articleImages/6.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
	</body>
</html>
<script type="text/javascript">
	//匿名函数 也就是说没有函数名
	var a=function(){
		document.write("匿名函数"+"<br />");
	}
	a();
	var b=function(x){
		document.write(x);
	}
	b(6);
	//区别就是把函数名放在了变量的位置
</script> 
```
运行结果:
![在这里插入图片描述](https://img-blog.csdnimg.cn/f7399955af74478c825d3b1b150a65c5.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBASVQtQXVyb3Jh,size_20,color_FFFFFF,t_70,g_se,x_16)
附加题:js写导航条效果
方式1:

```
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
				width: 720px;
				list-style: none;
				display: flex;
				margin: 30px auto;
				/*border: 2px solid red;*/
			}
			li{
				background-color: pink;
				width: 80px;
				text-align: center;
				padding: 10px 0;
				border: 2px solid black;
				transition: all 1s linear;
			}
			/*默认选中*/
			li:first-child{
				/*color: tomato;
				border-bottom: 5px solid red;*/
			}
		</style>
	</head>
	<body>
		<ul>
			<li>0</li>
			<li>1</li>
			<li>2</li>
			<li>3</li>
			<li>4</li>
			<li>5</li>
			<li>6</li>
			<li>7</li>
			<li>8</li>
			<li>9</li>
			<li>10</li>
		</ul>
	</body>
</html>
<script type="text/javascript">
	var liarray=document.getElementsByTagName("li");
	for(var i=0;i< liarray.length; i++){
		liarray[i].onclick=function(){
			//i的值留不住 要用关键字this
			this.style.color= "red";
			this.style.borderBottom = "6px solid blue";
			for(var j=0;j<liarray.length;j++){
			if(liarray[j]!=this){
				liarray[j].style.color="black";
				liarray[j].style.borderBottom="none";
				}
			}
		}
	}
</script>

```
运行结果:
![](https://img-blog.csdnimg.cn/c44af4269b654cdabb1bd3ce761bd8b4.png)
![](https://img-blog.csdnimg.cn/650dd0a271ae4c1d86109e5b6a9670fd.png)


方式2:

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
				width:800px;
				list-style: none;
				display: flex;
				margin: 30px auto;
				/*border: 2px solid red;*/
				position: relative;
			}
			li{
				background-color: pink;
				width: 80px;
				text-align: center;
				padding: 10px 0;
				border: 2px solid black;
			}
			div{
				width: 80px;
				height: 5px;
				background-color: blue;
				position: absolute;
				bottom: 0;
				left: 0;
				transition: all .5s linear;
			}
		</style>
	</head>
	<body>
		<ul>
			<li>0</li>
			<li>1</li>
			<li>2</li>
			<li>3</li>
			<li>4</li>
			<li>5</li>
			<li>6</li>
			<li>7</li>
			<li>8</li>
			<li>9</li>
			<!--这个div充当滑动的条-->
			<div id="slide"></div>
		</ul>
	</body>
</html>
<script type="text/javascript">
	var liArray=document.getElementsByTagName("li");
	for(var i=0;i< liArray.length; i++){
		liArray[i].style.cursor="pointer";
		liArray[i].onclick=function(){
			//this 就是当前被点击的标签对象
			//取下标
//			this.style.cursor="pointer";
			var index=0;//用来记录this下标
			for(var j=0;j< liArray.length; j++){
				if (this==liArray[j]) {
					index=j;//j的位置就是被点击的this下标
				}
			}
			//找到下滑位置
			slide.style.left=80*index+"px";
		}
	}
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/d2e0da96177a4a738c0f18e50b3a977d.png)

