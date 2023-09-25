---
title: jq语法基础
date: 2020-12-21 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/13.jpg
banner_img: ../articleImages/13.jpg
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
			div{
				background-color: red;
			}
		</style>
	</head>
	<body>
		<div id="one">id选择器</div>
		<div class="c1">c1选择器--div</div>
		<div class="c1">c1选择器--div</div>
		<p class="c1">c1选择器--p标签</p>
		<ul class="box">
			<li>列表1</li>
			<li>列表2</li>
			<li>列表3</li>
			<li>列表4</li>
			<li>列表5</li>
			<li>列表6</li>
		</ul>
	</body>
</html>

<!--第一步  就是引入jq框架 其实本质还是一个js文件!!!-->
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>

<script type="text/javascript">
	/*
	 jQuery 简称jq框架,其实就是对js原生语言的封装;
	 jq版本:  火狐和谷歌等浏览器兼容都很好
	 jQuery-1.xxx版本, 兼容ie6,7,8浏览器    
	 jQuery-2.xxx及其以上版本, 不兼容ie6,7,8 浏览器
	 
	 jQuery的优势:
	 1.HTML标签获取   $()
	 2.HTML元素操作  取值,赋值,属性等操作
	 3.CSS样式操作  
	 4.动画操作
	 5.事件
	 6.DOM操作
	 7.AJAX网络请求
	 注意:js的语法特点都是 变量 = 值; 
	 jq中,注意了---几乎没有 =  ;并且写事件不带on!
	 */
	//1.jq获取标签的方式
	//格式:  $("选择器")  就是要获取的标签!!!
	console.log($("#one"));
	console.log($(".box li"));
	console.log($(".box li:first-child"));
	console.log($(".c1"));
	//jq对象可以调用jq方法
	//能不能写js对象?  肯定是可以的!!!
	var one = document.querySelector("#one");
	//js对象如何修改css样式?
	one.style.backgroundColor = "palevioletred";
	//jq对象如何修改css样式呢?
	$(".box li:first-child").css("background-color", "#6A5ACD");
	//如何同时修改多个元素的样式呢?------------------------
	//js原生!!!!
	var liArray = document.querySelectorAll(".box li");
	for(var i = 0; i < liArray.length; i++){
		liArray[i].style.backgroundColor = "yellowgreen";
	}
	//jq多牛皮!!!!!!!  同时修改多个元素的css样式!!
	$(".c1").css("background-color", "deepskyblue");
	//因为在jq中,程序只查看你是否找到了标签!!并不管标签有几个!!!这就是封装的牛皮之处!!
	//如何同时修改多个样式呢?  {}写法 属性名没有提示!!
	$(".c1").css({
		width:'300px',
		height:"100px"
	});
	//如何给不同的标签设置不同的css样式呢????
	//函数参数(元素的下表, 当前元素的css值)
	function randomColor(){
		var red = Math.floor(Math.random() * 256);
		var green = Math.floor(Math.random() * 256);
		var blue = Math.floor(Math.random() * 256);
		return "rgb(" + red + "," + green + "," + blue + ")";
	}
	
	$(".c1").css("background-color", function(index, value){
//		console.log("下标", index, ";元素的背景色", value);
		//想给不同的标签设置不同的样式值 就把css值 返回即可!!!
		return randomColor();
	})
	//练习:给不同的标签设置不同的高度
	$(".c1").css("height", function(index, value){
		return (index + 1) * 100;  //jq对单位要求不严格!!可以不带单位
	})
	
	$(".c1").css("width", function(index, value){
		return Math.floor(Math.random() * 301 + 100);
	})
	
	
</script>
```
![](https://img-blog.csdnimg.cn/673e091febe44816b64787292801748b.png)


