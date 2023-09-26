---
title: jq语法中的类选择器
date: 2020-12-22 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/14.jpg
banner_img: ../articleImages/14.jpg
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
			.root{
				background-color: salmon;
			}
		</style>
	</head>
	<body>
		<!--div{div$}*4-->
		<div>div1</div>
		<div>div2</div>
		<div>div3</div>
		<div>div4</div>
		
		<button id="btn">点击切换样式</button>
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>

<script type="text/javascript">
	//js中如何给标签设置class选择器  只能一个一个 获取标签对象才能.className
	var div1 = document.querySelector("div:first-child");
	div1.className = "c1";
	
	
	
	//jq中  既可以给1个标签设置 也可以同时设置多个标签  因为不写for循环
	$("div").addClass("one");
	//想添加不同的class
	$("div").addClass(function(index, value){  //value 是当前标签正在显示的class值
		console.log(index, value);
		return "div" + (index + 1);
	});
	//如果添加的值 没有规律!!
	var classArray = ["root", "box", "header", "content"]; //0--3
	$("div").addClass(function(index, value){
		return classArray[index]; //标签下标刚好也是0--3  
	})
	//---------------------------------
	//删除class 
	$("div").removeClass("c1");
	$("div").removeClass("one");
	//怎么添加的就怎么删掉!!!
	$("div").removeClass(function(index, value){
		return "div" + (index + 1);
	})
	$("div").removeClass(function(index, value){
		return classArray[index];
	})
	//---------------------------------------------
	//既能添加还能删除     如果不存在此class值,就是添加! 如果已存在此class值,就是删除!
   $("#btn").click(function(){
   	$("div").toggleClass("root");
   })

	//写法同上!!!
	
	
</script>
```
![](https://img-blog.csdnimg.cn/9d4f2408cf8546368c8ccd3681b43839.png)
![](https://img-blog.csdnimg.cn/319a4b3b61824926b8b411fd185b22ba.png)

