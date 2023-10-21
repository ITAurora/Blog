---
title: jq中的动画
date: 2021-1-3 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/9.jpg
banner_img: ../articleImages/9.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>


```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>jq中的动画</title>
		<style type="text/css">
			div{
				width: 200px;
				height: 200px;
				margin-right: 20px;
				margin-bottom: 30px;
				float: left;
			}
			#a{
				background-color: palegreen;
			}
			#b{
				background-color: palevioletred;
			}
			#c{
				background-color: gold;
			}
			
			
		</style>
	</head>
	<body>
		<div id="a"></div>
		<div id="b"></div>
		<div id="c"></div>
		
		<hr style="clear: both;" />
		
		<button id="hide">隐藏</button>
		<button id="show">显示</button>
		<button id="teshu1">特殊效果1</button>
		
		<button id="fadeIn">淡入</button>
		<button id="fadeOut">淡出</button>
		<button id="teshu2">特殊效果2</button>
		<button id="teshu3">特殊效果3</button>
		
		<button id="slideUp">上拉</button>
		<button id="slideDowm">下拉</button>
		<button id="teshu4">特殊效果4</button>
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>

<script type="text/javascript">
	//1.第一组 隐藏/显示
	$("#hide").click(function(){
		$("#a").hide(800);
		/*
		动画时间,可以写数字  毫秒
		也可以 slow, normal, fast
		*/
		$("#b").hide("slow");
		$("#c").hide(1000, function(){
			console.log("动画结束才会执行此函数!!!");
		})
	})
	
	$("#show").click(function(){
		$("#a").show(300);
		$("#b").show("normal");
		$("#c").show(2000, function(){
			console.log("动画执行完毕!展示show");
		})
	})
	
	//特殊1 就是偷狗 toggle  即可显示有可隐藏
	$("#teshu1").click(function(){
		$("#a").toggle(1000);
		$("#b").toggle("fast");
		$("#c").toggle(1000, function(){
			console.log("特殊效果1!!动画完毕!");
		})
		
	})
	//--------------------------------------------------------
	//2.淡出淡出动画效果   关键单词:fade
	$("#fadeOut").click(function(){
		$("#a").fadeOut(500);
		$("#b").fadeOut("slow");
		$("#c").fadeOut(1000, function(){
			console.log("淡出效果动画结束!");
		})
	})
	
	$("#fadeIn").on("click", function(){
		$("#a").fadeIn(600);
		$("#b").fadeIn("fast");
		$("#c").fadeIn(2000, function(){
			console.log("淡入效果动画结束!!");
		})
	})
	
	//变化到指定的透明度
	$("#teshu2").click(function(){
//		fadeTo(动画时间, 透明度值, 函数)
		$("#a").fadeTo(1200, 0.3);
		$("#b").fadeTo("slow", 0.5);
		$("#c").fadeTo( 1000, 0.2, function(){
			console.log("透明度变化结束!!");
		})
	})
	
	//既可淡出也可淡出  fadeToggle()
	$("#teshu3").click(function(){
		$("#a").fadeToggle(1000);
		$("#b").fadeToggle("slow");
		$("#c").fadeToggle("fast", function(){
			console.log("特殊效果3执行结束!");
		})
	})
	//---------------------------------------------------
	//3.上拉下拉动画
	$("#slideUp").click(function(){
		$("#a").slideUp(1000);
		$("#b").slideUp("slow");
		$("#c").slideUp(800, function(){
			console.log("上拉动画结束!");
		})
	})
	
		$("#slideDowm").click(function(){
		$("#a").slideDown(1000);
		$("#b").slideDown("slow");
		$("#c").slideDown(800, function(){
			console.log("下拉动画结束!");
		})
	})
		
		$("#teshu4").click(function(){
		$("#a").slideToggle(1000);
		$("#b").slideToggle("slow");
		$("#c").slideToggle(800, function(){
			console.log("上拉/下拉动画结束!");
		})
	})
</script>

```
![](https://img-blog.csdnimg.cn/347f7e66447b489aac69c37286a3e1d8.png)
