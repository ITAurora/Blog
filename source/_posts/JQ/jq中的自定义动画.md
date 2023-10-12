---
title: jq中的自定义动画
date: 2020-12-27 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/2.jpg
banner_img: ../articleImages/2.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>jq中的自定义动画</title>
		<style type="text/css">
			#one{
				width: 200px;
				height: 200px;
				background-color: sandybrown;
			}
		</style>
	</head>
	<body>
		<div id="one"></div>
	</body>
</html>

<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>


<script type="text/javascript">
	//自定义动画 
  //特点:只有数字值才会有动画效果,例如宽高 透明度 margin left top等
  //例如背景色是没有动画效果的! 因为其值是字符串!!
	
	$("#one").animate({
		width:500,
		height:500,
		backgroundColor:"red",
		borderRadius:"50%",
		marginLeft:200
	}, 2000, "linear", function(){
		console.log("动画结束才会执行此处代码!!!");
		$("#one").css("background-color", "green");
	}).stop();  //动画刚开始就结束啦!! stop()用来停止动画!!!
	
	//动画停止 是stop()
	//jq中 点语法连续操作 
	
</script>

```
![](https://img-blog.csdnimg.cn/cde9706fbded47b9846bb0ec1c8f4659.png)
