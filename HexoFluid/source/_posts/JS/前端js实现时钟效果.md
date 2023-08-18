---
title: 前端js实现时钟效果
date: 2020-11-13 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/11.jpg
banner_img: ../articleImages/11.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>



```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>时钟效果</title>
		<link rel="stylesheet" type="text/css" href="css/时钟.css"/>
	</head>
	<body>
		<!--底部的div-->
		<div class="wrap">
			<!--  ul>(li>span{$})*12 -->
			<ul class="number center">
				<li><span>9</span></li>
				<li><span>10</span></li>
				<li><span>11</span></li>
				<li><span>12</span></li>
				<li><span>1</span></li>
				<li><span>2</span></li>
				<li><span>3</span></li>
				<li><span>4</span></li>
				<li><span>5</span></li>
				<li><span>6</span></li>
				<li><span>7</span></li>
				<li><span>8</span></li>
				
			</ul>
			<!--时针区域-->
			<ul id="pointer" class="center">
				<li id="hour"></li>
				<li id="minute"></li>
				<li id="second"></li>
				<!--按扣-->
				<div id="kou" class="center"></div>
			</ul>
		</div>
	
	
			<script src="js/时钟.js" type="text/javascript" charset="utf-8"></script>
	</body>
</html>

```
css文件代码:

```css
*{
	margin: 0;
	padding: 0;
}
ul{
	list-style: none;
}
.wrap{
	position: relative;
	width: 500px;
	height: 500px;
	margin: 30px auto;
	border-radius: 50%;
	box-shadow: 0 0 25px 2px black;
	background-image: linear-gradient(to bottom, #fff 2%, lightgray 15%, lightgray 86%, #fff);
}

.number{
	width: 460px;
	height: 460px;
	background-color: white;
	border-radius: 50%;
	/*阴影默认向外  inset可以设置隐藏向内*/
	box-shadow: 0 0 15px inset;
}

.center{
position: absolute;	
top: 0;
bottom: 0;
left: 0;
right: 0;
margin: auto;
}

/*----数字调整----*/
.number li{
	width: 100%;
	height: 50px;
	position: absolute;
	top: 0;
	bottom: 0;
	margin: auto 0;
	/*background-color: salmon;*/
	/*--*/
	line-height: 50px;
	font-size: 40px;
}
.number li span{
	margin-left: 15px;
	/*行元素 的transform属性效果失效*/
	display: inline-block;
}
/*-------------------------*/
/*时针区域*/
#pointer{
	width: 30px;
	height: 30px;
	border-radius: 50%;
	background-color: #333;
}

#pointer li{
	position: absolute;
	top: 0;
	bottom: 0;
	left: 50%;
	margin: auto 0;
	border-radius:0 50%  50% 0;
	/*修改旋转中心点!*/
	transform-origin: left center; 
	
}
#hour{
	width: 120px;
	height: 10px;
	background-color: firebrick;
}
#minute{
	width: 160px;
	height: 6px;
	background-color: darkgreen;
}
#second{
	width: 210px;
	height: 4px;
	background-color: gold;
}
#kou{
	width: 16px;
	height: 16px;
	border-radius: 50%;
	background-color: #fff;
}





```

js文件代码:

```javascript
//1.获取标签
var numberEL = document.getElementsByClassName("number")[0];
var numberArray = numberEL.getElementsByTagName("li");
var spanArray = numberEL.getElementsByTagName("span");

//功能区域 
//1.让数字所在的li 旋转
for(var i = 0; i < numberArray.length; i++){
	numberArray[i].style.transform = "rotateZ(" + i * 30 + "deg)";
	spanArray[i].style.transform = "rotateZ(" + (-i * 30) + "deg)"; 
}


//2.通过当前时间  来控制指针的旋转角度
function showTime(){
	//获取当前时间
	var now = new Date();
	//小时
	var h = now.getHours();
	//分钟
	var m = now.getMinutes();
	//秒
	var s = now.getSeconds();
	
	//设置秒针的旋转角度  1圈是360度 = 秒针动60下转一圈 
	//那么1秒 就是 6度
	second.style.transform = "rotateZ(" + (s * 6 - 90)+ "deg)";
	//设置分针的旋转角度  1圈是360度 = 分针动60下 一圈   一分钟=6度
	//例如： 3分30秒   分针应该是3*6 +  30 / 60 * 6
	minute.style.transform = "rotateZ(" + (m * 6 + s / 60 * 6  - 90) + "deg)";
	//时针  3时40分   60分钟=1小时=30度   3*30 + 40 / 60 * 30
	hour.style.transform = "rotateZ(" + (h * 30 + m / 60 * 30 - 90) + "deg)";
}


showTime();
setInterval(showTime, 1000);
```

运行结果:
![](https://img-blog.csdnimg.cn/9ac823893a1e49ec8bc2f9517de6a1a4.png)
