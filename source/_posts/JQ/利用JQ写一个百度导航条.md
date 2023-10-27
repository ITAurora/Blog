---
title: 利用JQ写一个百度导航条
date: 2021-1-7 10:10:10
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
		<meta charset="utf-8">
		<title>百度导航栏</title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			.root{
				width: 100%;
				height: 40px;
				background-color: darkblue;
				margin-top: 50px;
			}
			.root ul{
				list-style: none;
				width: 900px;
				margin: 0 auto;
				height: 40px;
				line-height: 40px;
				color: white;
				/* background-color: salmon; */
				font-weight: bold;
				position: relative;
			}
			.root ul li{
				float: left;
				text-align: center;
				width: 65px;
				position: relative;
				z-index: 1;
			}
			.root ul li:first-of-type{
				background-color: darkred;
			}
			/* 设置滑块 */
			.slide{
				width: 65px;
				height: 40px;
				background-color: darkred;
				position: absolute;
				left: 0px;
				top: 0;
			}
			
		</style>
	</head>
	<body>
		<div class="root">
			<ul>
				
				<li>首页</li>
				<li>国内</li>
				<li>国际</li>
				<li>军事</li>
				<li>财经</li>
				<li>娱乐</li>
				<li>体育</li>
				<li>互联网</li>
				<li>科技</li>
				<li>游戏</li>
				<li>女人</li>
				<li>汽车</li>
				<li>房产</li>
				<!-- 滑块 -->
				<div class="slide"></div>
			</ul>
		</div>
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>
<script type="text/javascript">
	//定义变量 先记录当前选中的导航的下标
	var index = 0;
	//点击事件
	$(".root ul li").click(function(){
		$(this).css("background-color","darkred").siblings("li").css("background-color","transparent");
		//记录下标
		index = $(this).index();
	})
	//添加鼠标滑动事件  只要鼠标触摸 就让滑块滑动
	$(".root ul li").mouseenter(function(){
		$(".slide").stop().animate({
			left: $(this).index() * $(this).innerWidth(),
		},300,"linear")
	})
	
	//鼠标离开事件   但是 加给ul
	
	$(".root ul").mouseleave(function(){
		$(".slide").stop().animate({
			left:index * $("li").innerWidth(),
		})
	})
	
	
	
</script>

```
![](https://img-blog.csdnimg.cn/f111a94c35e64a77886d366ac31225ba.png)
