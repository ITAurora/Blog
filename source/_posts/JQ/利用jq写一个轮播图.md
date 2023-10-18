---
title: 利用jq写一个轮播图
date: 2020-12-30 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/5.jpg
banner_img: ../articleImages/5.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>淘宝轮播图</title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			
			.root{
				width: 520px;
				height: 280px;
				border: #FFD700 3px solid;
				margin: 30px auto;
				position: relative;
				overflow: hidden;
			}
			.content{
				width: 3120px;
				height: 280px;
				position: absolute;
				left: 0;
			}
			.content img{
				float: left;
			}
			
		</style>
	</head>
	<body>
		<div class="root">
			<div class="content">
				
				<img src="img/t1.png"/>
				<img src="img/t2.jpg"/>
				<img src="img/t3.jpg"/>
				<img src="img/t4.jpg"/>
				<img src="img/t5.jpg"/>
				<img src="img/t1.png"/>
			</div>
		</div>
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>


<script type="text/javascript">
	//定义遍历 记录当前正在显示的图片的下标
	var imgIndex = 0;
	//1.封装自动轮播
	function autoChange(){
		imgIndex++;
		$(".content").animate({
			left: -imgIndex * 520,
		}, 800, "linear", function(){
			//此函数 特别重要!!  因为此位置是每次动画结束!都会执行!而且此处代码没有动画效果!!!
			if(imgIndex == 5){
				imgIndex = 0;
				//并且  立刻修改content的left值
				
				$(".content").css("left", "0");
			}
			
		})
		
	}
	//定义计时器
	var timer =setInterval(autoChange, 1200);
	
	
	
</script>
```
![](https://img-blog.csdnimg.cn/11d2ec889d69404f8f88d1ddc92d61fe.png)
