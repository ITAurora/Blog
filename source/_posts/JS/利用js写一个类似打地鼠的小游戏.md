---
title: 利用js实现一个打地鼠的小游戏
date: 2020-11-24 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/15.jpg
banner_img: ../articleImages/15.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

**代码仅供参考**
css代码;

```css
*{
	margin: 0;
	padding: 0;
}
a{
	text-decoration: none;
}

.root{
	width: 320px;
	height: 480px;
	background:url(../img/game_bg.jpg);
	margin: 30px auto;
	position: relative;
}

/*分数*/
.score{
	position: absolute;
	left: 60px;
	top: 12px;
	color: white;
	font-weight: bold;
}

/*进度条*/
.progress{
	background: url(../img/progress.png) no-repeat;
	width: 180px;
	height: 16px;
	position: absolute;
	left: 63px;
	top: 66px;
	
}

/*设置狼的图片*/
.wolfs img{
	cursor: pointer;
	position: absolute;
}

/*------*/
/*设置开始游戏菜单*/
.menu{
	position: absolute;
	left: 0;
	top: 200px;
	width: 320px;
	text-align: center;
}
.start, .handle, .gameover{
	font-size: 32px;
	font-weight: bold;
	line-height: 50px;
	color: orangered;
	text-shadow: 0 0 5px yellow;
}

.gameover{
	width: 320px;
	position: absolute;
	left: 0;
	top:200px;
	text-align: center;
	/*默认隐藏*/
	display: none;
}

```

html代码:
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
		<link rel="stylesheet" type="text/css" href="css/打狼.css"/>
	</head>
	<body>
		<!--底部的div-->
		<div class="root">
			<!--显示分数-->
			<div class="score">0</div>
			<!--显示剩余时间的进度条-->
			<div class="progress"></div>
			<!--灰太狼或者小灰灰出现的标签-->
			<div class="wolfs">
				<!--<img src="img/h5.png"/>-->
			</div>
			<!---------------------->
			<!--开始游戏菜单 menu菜单-->
			<div class="menu">
				<a href="###" class="start">开始</a> <br />
				<a href="###" class="handle">游戏操作助手</a>
			</div>
			<!--结束游戏菜单-->
			<div class="gameover">
				game over
			</div>
		</div>
	</body>
</html>
<script src="js/打狼.js" type="text/javascript" charset="utf-8"></script>

```
js代码:

```js
//获取标签
//1.开始按钮
var startBtn = document.querySelector(".start");
//2.倒计时进度条
var progressEl = document.querySelector(".progress");
//3.分数
var scoreEl = document.querySelector(".score");
//4.灰太狼所在的div
var wolfDiv = document.querySelector(".wolfs");
//5.获取开始游戏菜单
var menuEL = document.querySelector(".menu");
//6.获取游戏结束菜单
var gameOver = document.querySelector(".gameover");
//-------------------------------
//2.定义变量
//进度条的长度  因为需要实时修改其长度 进行倒计时器操作
var progressWidth = progressEl.offsetWidth;
//定义创建狼的计时器
var createWolfTimer;
//定义变量 用于记录上一个狼出现的位置!!
var lastIndex = -1;
//随机出现在9个洞口的定位值
var positionArray = [{
     l: "98px",
     t: "115px"
    }, {
     l: "17px",
     t: "160px"
    }, {
     l: "15px",
     t: "220px"
    }, {
     l: "30px",
     t: "293px"
    }, {
     l: "122px",
     t: "273px"
    }, {
     l: "207px",
     t: "295px"
    }, {
     l: "200px",
     t: "211px"
    }, {
     l: "187px",
     t: "141px"
    }, {
     l: "100px",
     t: "185px"
    }];
//-------------------------
//3.封装函数
function randomNum(min, max){
	return Math.floor(Math.random() * (max - min + 1) + min);
}

//封装进度条倒计时
function progressChange(){
	//设置倒计时计时器
	var progressInterval = setInterval(function(){
		progressWidth -= 2;
		//如果图片宽度减为0
		if(progressWidth < 0){
			//游戏结束!!!
			gameOver.style.display = "block";
			//进度条计时器 需要清除
			clearInterval(progressInterval);
			//清除创建狼的计时器 因为游戏时间结束
			clearInterval(createWolfTimer);
		}
		//要把实时在修改的宽度 赋值给标签
		progressEl.style.width = progressWidth + "px";
		
	}, 100)

}

//点击开始按钮的点击事件
startBtn.onclick = function(){
	//1.先隐藏开始菜单 menu
	menuEL.style.display = "none";
	//2.开始倒计时 进度条
	progressChange();
	//3.随机出现狼   我们已经声明过此计时器
	createWolfTimer = setInterval(function(){
		//创建用来显示狼的img 
		var wolfImg = document.createElement("img");
		//关键! 随机概率  是灰太狼还是小灰灰
		//给对象新增属性 
		//用随机数1--100,来判断是否大于20; 大于20的概率较大,所以取走h
		//而且灰太狼he小灰灰的图片名字 仅仅就是相差 h 还是 x这个字母!!后面的路径可以拼接!!!
		wolfImg.type = randomNum(1, 100) > 20 ? "h" : "x";
		//设置狼出现时 图片的名字编号  默认肯定是从第一张开始 也就是0
		wolfImg.index = 0;
		//设置图片路径
		wolfImg.src = "img/" + wolfImg.type + wolfImg.index + ".png";
		//随机狼出现的位置
		var wolfIndex = randomNum(0, positionArray.length - 1);
		//------------第二节  新增功能-----------
		//避免连续在同一个洞口出现
		while(true){
			if(wolfIndex == lastIndex){
				//说明本次随机 跟 上次随机一致
				wolfIndex = randomNum(0, positionArray.length - 1);
			}else{
				//说明 本次 和  上次不一样
				break;//结束循环!!!
			}
		}
		lastIndex = wolfIndex;//记录本次随机的下标  为下次做准备
		console.log(wolfImg.type);
		//-------------------第二节 到这里-------------------------------
		//------把随机到的位置  赋值给wolfImg显示
		wolfImg.style.left = positionArray[wolfIndex].l;
	    wolfImg.style.top = positionArray[wolfIndex].t;
		//关键一步  显示标签
		wolfDiv.appendChild(wolfImg);
		
		//------注意!!写个计时器 模拟狼上升的动画效果
		wolfImg.upTimer = setInterval(function(){
			//切换图片  其实就是不停的修改  wolfImg.index 属性
			wolfImg.index++;
			if(wolfImg.index  > 4){
				//大于4  其实就是到了5
				//清除上升计时器
				clearInterval(wolfImg.upTimer);
				//按照道理 我应该把狼下降的计时器 放在这里写!!!
				wolfImg.downFunction();
			}
			//一定要修改标签的属性
			wolfImg.src = "img/" + wolfImg.type + wolfImg.index + ".png";
		}, 150);
		
		//-----------注意注意!! 再写计时器! 模拟狼下降的动画效果!!
		//封装函数  等上升结束之后  再调用此函数  再执行下降计时器
		wolfImg.downFunction = function(){
			wolfImg.downTimer = setInterval(function(){
				wolfImg.index--;
				if(wolfImg.index == 0){
					//清除下降的计时器
					clearInterval(wolfImg.downTimer);
					//注意!!我们每隔1秒 会创建新的img标签  所以这个img下降之后 就表示用户没有打到这个狼!不加分也不会减分! 那么此标签已经没用了!!
					wolfDiv.removeChild(wolfImg);
				}
			wolfImg.src = "img/" + wolfImg.type + wolfImg.index + ".png";

			}, 150)
			
		}
		
		//-------------第二节-------------------
		//注意!! 找bug!!! 如果点击过快  会重复加分/减分!!!
		//做个标记   默认为0  表示从来没点击过;   那一旦点击 就修改为1
		wolfImg.isFirstClick = 0;
		//给狼添加点击事件
		wolfImg.onclick = function(){
			//注意! 先判断标记值 是0  还是  1
			if(wolfImg.isFirstClick == 1){
				//已经被点击过了!!
				return; //直接结束这个点击事件函数
				//retun 结束它所在的函数!!
			}
			
			//注意!能执行此处  说明是第一次点  赶紧修改标记值 阻止下次点击
			wolfImg.isFirstClick = 1;
			//调用加分/减分的函数
			secoreChange(wolfImg);
			//注意注意!一旦点击了狼 那就是要加分或者减分啦  所以无论目前在上升还是下降 通过清除掉!!
			clearInterval(wolfImg.upTimer);
			clearInterval(wolfImg.downTimer);
			//切换图片  是加分 还是减分 都从图片5开始
			wolfImg.index = 5;
			//-----注意注意!写个计时器  模拟加分/减分的动画效果
			wolfImg.clickTimer = setInterval(function(){
				wolfImg.index++;
				if(wolfImg.index == 9){
					//已经到了最后一张图片啦 加分/减分动画可以结束啦!
					clearInterval(wolfImg.clickTimer);
					//同样 这个img已经无用   可以清除掉啦! 每秒种都会创建新的img
					wolfDiv.removeChild(wolfImg);
				}
			
			wolfImg.src = "img/" + wolfImg.type + wolfImg.index + ".png";

			}, 150)
			
		
		}
		
		
	}, 1000)

	
}

//处理得分还是减分的函数
function secoreChange(img){
	if(img.type == "h"){
	scoreEl.innerHTML = parseInt(scoreEl.innerHTML) + 10;
		
	}else{
		scoreEl.innerHTML -= 10;
	}
	
}

```
