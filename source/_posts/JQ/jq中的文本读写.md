---
title: jq中的文本读写
date: 2020-12-24 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/16.jpg
banner_img: ../articleImages/16.jpg
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
		<div></div>
		<h2></h2>
		<p></p>
		
		<input type="text" placeholder="这个属性不影响"/>
	</body>
</html>
	<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>


<script type="text/javascript">
	//重点  分清楚,什么是js变量! 什么是jq变量!!
	var div = document.querySelector("div");
	//js中 给标签写入数据
	div.innerHTML = "<a href='###'>百度</a>";
	div.innerText += "只能识别字符串!!!";
	//新数据覆盖旧数据!!!
	//怎么样才能让js对象,变为jq对象!!!
	//语法格式: $(js变量)
	$(div).css({
		width:300,
		height:100,
		backgroundColor:"pink"
	});
	
	//来jq中 文本的读写
	$("h2").html("<strong>加粗标签!要放假啦!!</strong>")
	$("h2").text($("h2").text() + "只能识别字符串!!"); //新数据覆盖旧数据!!
	//对标签文本取值
	console.log($("h2").text());
	//做文本拼接  首选就是  html()
	$("h2").html("新数据拼接" + $("h2").html());
	
	$("h2").css("background-color", "skyblue");
	
	//------------------------------------------------
	// val()  专门针对form表单系列的标签进行 取值 和  赋值操作!!
	$("input").val("给输入框标签赋值!!!")
	//取值也是val()
	console.log($("input").val());
</script>
```
![](https://img-blog.csdnimg.cn/924cee45ac5048b7ad472e6daaf5052b.png)
