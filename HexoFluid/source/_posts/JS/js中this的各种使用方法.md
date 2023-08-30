---
title: js中this的各种使用方法
date: 2020-11-25 10:10:10
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
	</head>
	<body>
		<ul>
			<li>列表1</li>
			<li>列表2</li>
			<li>列表3</li>
		</ul>
	</body>
</html>
<script type="text/javascript">
	//this的第一种情况!!!!!!!!!!!!!!!
	var li = document.querySelectorAll("li");
	for(var i = 0; i < li.length; i++){
		li[i].onmouseenter = function(){
			console.log(this);
			//在事件中!包括点击事件,鼠标事件等!!
			//this指代被点击的标签对象!
		}
	}
	
	//this的第二种情况
	var stu = {
		name:"王二狗子",
		sex:"男",
		age:18,
		hobby:["", "", ""],
		run:function(){
			console.log(this); //在对象   this就指代当前对象!!
//			console.log("狗子在奔跑!!!");
		}
	};
	//此时  this指代当前函数所属对象!!
	stu.run();
	console.log(stu);
	
	//this的第三种情况
	console.log(this);//指代window 因为全局变量/函数等都属于window
	function aaa(){
		console.log(this);//指代window
	}
    aaa();
	
</script>

```
测试:
![](https://img-blog.csdnimg.cn/7e7b6f66c4974d3e86b66213393e94dd.png)
