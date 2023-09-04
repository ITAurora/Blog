---
title: 前端js中array数组的使用
date: 2020-11-09 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/3.jpg
banner_img: ../articleImages/3.jpg
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
		<div class="">
			
		</div>
	</body>
</html>
<script type="text/javascript">
	//数组:本质是一个变量 是多个数的集合
	//数组英文 array
	//数组是object类型
	var arr=[1,2,3,4,"哈哈","呵呵",true,
	undefined,NaN];
	console.log(arr,typeof arr);
	var divarray =document.getElementsByTagName("div");
	console.log(divarray,typeof divarray);
	//{}是对象的标志
	var stu={
		name:"123",
		age:18
	}
	console.log(stu,typeof stu);
	var arr=[1,2,3,4,"哈哈","呵呵",true,
	undefined,NaN,stu];
	console.log(arr,typeof arr);
	//length 数组长度
	for(var i = 0; i <= arr.length; i++){
		document.write(arr[i]+'<br />');
		}
</script>
```
运行结果：
![](https://img-blog.csdnimg.cn/8ce57539af354918b28b281c6ee2ebe1.png)
控制台
![](https://img-blog.csdnimg.cn/ec19f744e7c3411a99fba0645c0bd530.png)

数组合并

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
	var a=[];
	for (var i=0;i<10;i++){
		a[i]=Math.floor(Math.random()*71+10);
	}
	document.write(a+"<br />");
	var a=[];
	var b=[];
	var c=[];
	for (var i=0;i<5;i++){
		a[i]=Math.floor(Math.random()*51+30);
		b[i]=Math.floor(Math.random()*51+30);
		c[i]=a[i];
		c[i+5]=b[i];
	}
	document.write(a+"<br />");
	document.write(b+"<br />");
	document.write(c+"<br />");
</script>
```
运行结果：
![](https://img-blog.csdnimg.cn/574146532b624a97a0210d414916e542.png)

