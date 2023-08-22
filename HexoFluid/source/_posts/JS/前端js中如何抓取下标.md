---
title: 前端js中如何抓取下标
date: 2020-11-17 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/1.jpg
banner_img: ../articleImages/1.jpg
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
	//对象
	//num name 等这些都是对象的特点特征,程序称其为"属性和行为 "
	var stu={
		num:1,
		name:"王二狗子",
		sex:"男",
		age:18,
		hobby:["琴","棋","书","画"],
		run:function(){
			document.write("哈撒给<br />");
		}
	};
	document.write(stu+"<br />");
	//点语法
	document.write(stu.name+"<br />");
	//利用索引 和arr[0]同一原理
	document.write(stu["name"]+"<br />");
	//新增属性
	stu.phone=123456789;
	document.write(stu.phone+"<br />");
	//修改属性值
	stu.name="王二麻子";
	document.write(stu.name+"<br />");
	//属性值也可以是数组 同样可以遍历
	for(var i=0;i<stu.hobby.length;i++){
		document.write(stu.hobby[i]+"<br />");
	}
	//调用对象里的函数
	stu.run();
	//---------------------------------------
	
	var liArray=document.getElementsByTagName("li");
	for (var i=0;i<liArray.length;i++) {
		liArray[i].index=i;
		document.write(liArray[i].index+"<br />");
		liArray[i].onclick=function(){
			document.write(this.index);
		}
	}
</script>

```
运行结果：
![](https://img-blog.csdnimg.cn/fac2f1466aa549398db7e3c38c9f0601.png)
点击：
![](https://img-blog.csdnimg.cn/72f81fd14a5d4f359cf256f61422ddac.png)

