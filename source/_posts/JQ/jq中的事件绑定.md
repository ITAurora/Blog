---
title: jq中的事件绑定
date: 2020-12-23 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/15.jpg
banner_img: ../articleImages/15.jpg
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
		<div>div1</div>
		<div>div2</div>
		<div>div3</div>
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>

<script type="text/javascript">
	//练习:修改css  jq对单位不要求   但是写了单位就是字符换  ""
	$("div").css({
		width:200,
		height:"200px",
		backgroundColor:"pink",
		margin:20
	})
	//jq中事件绑定
	//方式1
	$("div:first-child").click(function(){
		console.log("div1被点击了!!!");
	})
	
	$("div:first-child").mouseenter(function(){
		console.log("鼠标进入div1啦!!");
	})
	
	//方式2: 使用on关键字  on(事件类型, 函数)
	$("div:nth-child(2)").on("click", function(){
		console.log("div2被点击啦!!");
	});
	
	
	
	//在jq3.0版本之前  还可以使用  标签.bind(事件类型, 函数)
	//在3.0版本后bind被弃用!! 所以以后万一见到了就等价于 on() 
	
	//方式2还可以这么写
	function aaaa(){
		console.log("单独把函数写出来!!双击击了div3");
	}
	$("div:nth-child(3)").on("dblclick", aaaa); //函数不要带()  函数() 是调用函数
	$("div:nth-child(3)").on("dblclick", function(){
		console.log("这是div3的另一个双击事件!!!");
	})
	//-----------------------------------------
	//以后再取消事件 不用再赋值为null
	//jq中可以关闭事件!!! off
	$("div:first-child").off("click");//关闭div1的点击事件!!!
	
	//问题: div3有两个双击事件, 我该如何选择结束aaaa这个事件呢??
	$("div:nth-child(3)").off("dblclick", aaaa);
	//---------------------------------------------------------------------
	//还有  其他鼠标事件  键盘事件  移动端事件  表单事件
	//还有一个特殊  模仿css中的hover选择器
	//其实就是一个鼠标进入 和  鼠标离开的结合写法!!!!!!!
	$("div").hover(function(){
		console.log("鼠标来了!");
		//jq版本的 this
		$(this).css("background-color", "seagreen");
	}, 
	function(){
		console.log("鼠标走了!!");
		$(this).css("background-color", "pink");
	})
	
</script>
```
![](https://img-blog.csdnimg.cn/f6559ed0049249c09510d37dd61ccb23.png)
