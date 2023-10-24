---
title: jq中的属性操作
date: 2021-1-4 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/10.jpg
banner_img: ../articleImages/10.jpg
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
		<img src=""/>
		<img src=""/>
		<img src=""/>
		
		
		<a href="">百度</a>
		<div id="one"></div>
		
		
		<input type="checkbox" />
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>

<script type="text/javascript">
	//1.回顾js中的属性操作
	var img = document.querySelector("img");
	//方式1:
	img.src = "img/t1.png";
	//自定义属性
	img.type = "天猫图片";
	console.log(img.type);
	//方式2:
	img.setAttribute("src", "img/t1.png");
	//自定义属性
	img.setAttribute("index", "第一张");
	console.log(img.getAttribute("index"));
	//------------------------------------------------------------
	//2.看jq中如何操作!!!!
	/*
	 语法:
	 attr(属性名, 属性值或者函数);
	 如果需要为标签添加多个属性  可以使用{}对象形式添加
	 */
	
	$("a").attr("href", "http://www.baidu.com");
	//修改多个值
	$("img").attr({
		src:"img/t2.jpg",
		width:300
	});
	
	//获取属性值!!!
	console.log($("a").attr("href"));
	console.log($("img").attr("src"));
	
	//删除属性值
	$("img").removeAttr("width");
	$("a").removeAttr("href");
	
	//练习:给三个img 添加不同的三张图片
	var imgNameArray = [];
	$("img").attr("src", function(index, value){
		return "img/t" + (index + 2) + ".jpg";
	})
	//练习:给三个img标签  宽度依次减少100px
	$("img").attr("width", function(index, value){
		
		return 520 - (index + 1) * 100
	})
	//-------------------------------------------------------
	//操作属性的第二种方式    prop()
	//用法同attr()
	
	$("a").prop("href", "http://baidu.com");
	//多个属性
	$("div").prop({
		num:1,
		data:"自定义一个属性值"
	});
	//一样可以使用函数  
//	$("").prop("属性名", 函数)
   //获取值
   console.log($("div").prop("num"));
   console.log($("img").prop("src"));
	//删除
	$("a").removeProp("href");
	//------------------------------------
	/*
	 区别:
	 1.attr()以后多用于自定义属性操作
	 2.prop()多用于元素自带属性的操作,例如img的src a的href等
	 但是如果属性值是boolean类型,就要使用prop()方式访问属性值!!
	 */
	
	console.log($("input").prop("checked")); //有值 
	console.log($("input").attr("checked")); //undefined
</script> 
```
![](https://img-blog.csdnimg.cn/06b47c5f243343a887f7eda41429e336.png)
