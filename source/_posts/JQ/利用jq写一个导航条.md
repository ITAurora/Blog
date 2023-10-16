---
title: 利用jq写一个导航条
date: 2020-12-29 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/4.jpg
banner_img: ../articleImages/4.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>丝滑版导航条</title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			ul{
				list-style: none;
				width: 400px;
				height: 40px;
				line-height: 40px;
				border:2px solid gold;
				margin: 40px auto;
				display: flex;
				justify-content: space-between;
				text-align: center;
				position: relative;
			}
			li{
				width: 50px;
			}
			#slide{
				width: 40px;
				height: 2px;
				background-color: green;
				position: absolute;
				left: 5px;
				bottom: 4px;
				/*transition: all .3s linear;*/
			}
			
			
		</style>
	</head>
	<body>
		<ul>
			<li>娱乐</li>
			<li>军事</li>
			<li>历史</li>
			<li>财经</li>
			<li>民生</li>
			<li>汽车</li>
			<li>疫情</li>
			<li>国内</li>
			<div id="slide"></div>
		</ul>
		
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>

<script type="text/javascript">
	
	$("ul li").mouseenter(function(){
		//根据触摸的li的下标  动态修改slide的left值
//		$("#slide").css("left", $(this).index() * 50 + 5);
　　　　　　　$("#slide").stop().animate({
	           left:$(this).index() * 50 + 5
              }, 300)
		
	});
	
	
	
</script>
```
![](https://img-blog.csdnimg.cn/cc8fd37804b54f72a1e994fd04df557e.png)
