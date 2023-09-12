---
title: 利用js写一个飞翔小鸟小游戏
date: 2020-12-08 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/1.jpg
banner_img: ../articleImages/1.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

html部分
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
		<link rel="stylesheet" type="text/css" href="css/飞翔的小鸟.css"/>
	</head>
	<body>
		<!--最外层的标签-->
		<div id="root">
			<!--head 开始游戏界面上面的名字-->
			<div id="head">
				<img src="img/bird.png"/>
			</div>
			<!--开始菜单  -->
			<div id="menu">
				<img src="img/start.jpg"/>
			</div>
			<!--结束游戏菜单 默认隐藏-->
			<div id="end">
				<img src="img/message.jpg"/>
				<span id="currentScore">0</span>
				<span id="bestScore">0</span>
			</div>
			<!--顶部的分数-->
			<div id="score">
				<img src="img/0.jpg"/>
			</div>
			<!-------游戏音效 一会通过js控制播放--------->
			<audio src="music/bullet.mp3" id="bullet"></audio>
			<audio src="music/game_music.mp3" id="gameMusic"></audio>
			<audio src="music/game_over.mp3" id="gameOver"></audio>
			<!------------------------>
			<!--游戏开始之后   管道 和   飞扬的小鸟-->
			<!--管道 需要js动态创建 写父标签先占位置即可  pipe就是管道的意思!!-->
			<ul id="pipes">
				<!--准备写以下结构  管道有多个!! 不准用id选择器!!-->
				<!--<li class="pipe">
					<div class="upPipe"></div>
					<div class="downPipe"></div>
				</li>-->
			</ul>
			
			<!--飞扬的小鸟-->
			<img src="img/bird.png" id="bird"/>
			
		</div>
		<script src="js/飞扬的小鸟.js" type="text/javascript" charset="utf-8"></script>
	</body>
</html>

```
css部分
```css
*{
	margin: 0;
	padding: 0;
}

#root{
	background: url(../img/bg.jpg);
	width: 343px;
	height: 480px;
	margin:  40px auto;
	position: relative;
	/*--溢出隐藏*/
	overflow: hidden;
}

#head{
	width: 236px;
	height: 77px;
	background: url(../img/head.jpg);
	position: absolute;
	top: 100px;
	left: 53.5px;
}
#head img{
	position: absolute;
	right: 0;
	top: 25px;
	animation: birdFly 1.5s linear infinite;
}
/*游戏封面 小鸟上下的动画效果*/
@keyframes birdFly{
	0%{
		top: 25px;
	}
	25%{
		top: 0px;
	}
	50%{
		top: 25px;
	}
	75%{
		top: 50px;
	}
	100%{
		top: 25px;
	}
}
/*-------------------------------------*/
/*开始游戏菜单*/
#menu{
	width: 100%;
	text-align: center;
	top:280px;
	position: absolute;
}
#menu img{
	/*鼠标的状态*/
	cursor: pointer; 
}
/*------------------*/
/*结束游戏菜单  写完要隐藏*/
#end{
	width: 100%;
	text-align: center;
	position: absolute;
	top: 120px;
	font-size: 25px;
	display: none;
}
/*设置本局的分数  current 当前的;*/
#currentScore{
	position: absolute;
	left: 250px;
	top: 35px;
}
/*历史最高分*/
#bestScore{
	position: absolute;
	left: 250px;
	top: 90px;
}
/*顶部实时改变的分数*/
#score{
	width: 100%;
	/*要脱离文档流 因为小鸟和管道都要从页面滑过*/
	position: absolute;
	top: 0;
	text-align: center;
	display: none;
}
/*----------------------------------*/
/*管道  ul父标签*/
#pipes{
	list-style: none;
	height: 100%;
}
/*给子标签li 设置样式 一个li中有两个管道  上下两个*/
.pipe{
	width: 62px;
	height: 423px;
	background-color: yellow;
	position: absolute;
	left: 343px;
	top: 0;
}
/*分别给上下  两个管道设置样式  高度都应该由js随机 */
.upPipe{
	width: 100%;
	background: url(../img/up_pipe.png) bottom no-repeat, url(../img/up_mod.png) repeat-y;
	position: absolute;
	top:0;
	left: 0;
	/*height: 150px;*/
}

.downPipe{
	width: 62px;
	background: url(../img/down_pipe.png) top no-repeat, url(../img/down_mod.png) repeat-y;
	position: absolute;
	bottom: 0;
	/*height: 180px;*/
}
/*飞扬的小鸟 默认也要隐藏*/
#bird{
	position: absolute;
	left: 62px;
	top: 48%;
	display: none;
}

```
js部分
```js
//获取标签
//开始游戏按钮
var startBtn = document.querySelector("#menu img");
//游戏封面head  
var headEl = document.querySelector("#head");
//开始菜单
var menuEl = document.querySelector("#menu");
//结束菜单
var endEl = document.querySelector("#end");
//管道
var pipeUl = document.querySelector("#pipes");
//飞扬的小鸟
var birdImg = document.querySelector("#bird");
//游戏结束的本局分数
var currentScoreEL = document.querySelector("#currentScore");
//最高分
var bestScoreEl = document.querySelector("#bestScore");
//实时变化的分数 顶部的那个
var scoreEL = document.querySelector("#score");
//游戏音效 点击的声音
var bulletMusic = document.querySelector("#bullet");
//游戏进行的背景音乐
var gameMusic = document.querySelector("#gameMusic");
//游戏结束的时候音乐
var gameOverMusic = document.querySelector("#gameOver");
//底部的div  root 需要设置点击事件
var rootEl = document.querySelector("#root");



//----------------------------------------------------------
//2.补充变量
var num = 0;//记录分数
//用来模拟小鸟飞的速度
var speed = 0;
//小鸟下降的计时器
var birdDownTimer;
//小鸟上升的计时器
var birdUpTimer;



//3.封装函数
function randomNum(min, max){
	return Math.floor(Math.random() * (max - min + 1) + min);
}
//点击游戏开始按钮---------------------
startBtn.onclick = function(){
	//先阻止冒泡! 因为其父标签root 也有click点击事件
	event.stopPropagation();
	//或者
//	event.cancelBubble = true;
	//播放音乐 循环播放
	gameMusic.loop = true; //循环
	gameMusic.play();
	//隐藏开始菜单 和  head
	headEl.style.display = "none";
	menuEl.style.display = "none";
	//显示飞扬的小鸟 和 顶部的分数
	scoreEL.style.display = "block";
	birdImg.style.display = "block";
	//生成管道!!较为复杂,封装一下!!!!
	setInterval(createPipe, 3000);
	//小鸟下降--调用  需要计时器  最好写全局计时器  因为一旦点击屏幕小鸟会上飞,就需要取消下降计时器!!
	birdDownTimer = setInterval(birdDown, 20);
	//---在这里给root添加点击事件!! 也就是说 只要你点击了start开始按钮
	//root才能被点击!!!
	rootEl.onclick = clickRoot;//将函数赋值给点击事件 不要带()
	
	//--------------
//碰撞检测 只要游戏开始  就不停 检测
	
	setInterval(function(){
		
		//获取对应的li
	var liArray = document.querySelectorAll("li");
	for(var i = 0; i < liArray.length; i++){
		//判断li中 上下管道是否与小鸟碰撞
		crash(birdImg, liArray[i].firstElementChild);//上
		crash(birdImg, liArray[i].lastElementChild);//下
	  }
	
	}, 10)
	
	
	
	
}




//---------------------------------------------
//创建管道的函数!!!!!!!!!!!!!
function createPipe(){
	//创建li
	var li = document.createElement("li");
	li.className = "pipe";
	pipeUl.appendChild(li);
	//开始设置小鸟飞过的通道 
	//假设通道是 130px 
	var passHeight = 130;
	//随机一下上管道的高度     
	var upHeight = randomNum(80, 200);
	//总高度是li的高度是 423px   空隙是130px    上管道是随机[80, 200]  下管道?
	var downHeight = li.clientHeight - passHeight - upHeight;
	//继续创建上下两个管道的div
	var upDiv = document.createElement("div");
	upDiv.className = "upPipe";
    upDiv.style.height = upHeight + "px";
    li.appendChild(upDiv);
    var downDiv = document.createElement("div");
    downDiv.className = "downPipe";
    downDiv.style.height = downHeight + "px";
    li.appendChild(downDiv);
  console.log("上管道", upDiv.offsetLeft + "; 下管道" + downDiv.offsetLeft);
  console.log("管道父级li" + li.offsetLeft);
    //管道默认位置在距离父标签左侧 343px 刚好在游戏页面的右侧  需要动画向左滑动
    //li管道的当前位置
    var x = 343;
    //计时器 移动
    var pipeMoveTimer = setInterval(function(){
    	x--;
    	li.style.left = x + "px";
    	//一旦滑动到屏幕左边  就停止计时器 并且删除这个管道  管道宽度就是62
    	if(x <= -li.clientWidth){
    		clearInterval(pipeMoveTimer);
    		li.remove();
    	}
    	
    	//重点!小鸟距左62因为管道宽度也是62
    	if(x == 0){
    		//那不就说明 小鸟已经安全飞过管道了!!
    		//加分  ---封装函数 修改顶部实时变化的分数
    		changeScore();
    	}
    	
    	
    }, 10);
}
//封装函数--------修改分数
function changeScore(){
	num++;
	//清空现在正在现实的分数图片
	scoreEL.innerHTML = "";
	//添加图片
	if(num < 10){
		var img = document.createElement("img");
		img.src = "img/" + num + ".jpg"; //分数实时 变化 做路径拼接!!!
		scoreEL.appendChild(img);
	}else{
		//考虑100分以内  100分以外的自己写
		//双位数  十位
		var shiImg = document.createElement("img");
		//获取十位上的数字 
		var shi = Math.floor(num / 10);
		shiImg.src = "img/" + shi + ".jpg";
		scoreEL.appendChild(shiImg);
		//双位数的 个位
		var geImg = document.createElement("img");
		var ge = num % 10;
		geImg.src = "img/" + ge + ".jpg";
		scoreEL.appendChild(geImg);
	}
}

//--------------------------------------------------------
//小鸟的下降函数
function birdDown(){
	birdImg.src = "img/down_bird.png";
	//注意!我们让小鸟做变速动画  就是往下掉的越来越快  speed默认是0
	speed += 0.5;
	if(speed >= 10){
		speed = 10;
	}
	//就是修改计时器每隔20毫秒 往下降的间距值!!!
	
//	写个计时器 每隔100毫秒下降8px  这是匀速下降!! 也可以speed = 8;
//	如果是重力加速度下降!!  就是每隔一个时间段 下降距离越来越大!!
	//-----------------------------------------------------------
	birdImg.style.top = birdImg.offsetTop + speed + "px";
	//判断 小鸟是否落地
	//小鸟最大距上的top是   
	var maxTop = 423 - birdImg.clientHeight;
	if(birdImg.offsetTop >= maxTop){
		//游戏结束--封装函数 小鸟落地
		gameOver();
	}
	
}

//----游戏结束的函数
function gameOver(){
	//暂停游戏背景音乐
	gameMusic.pause();
	//播放游戏结束的音乐
	gameOverMusic.play();
	//清除所有的计时器! 不管是创建管道 还是小鸟在上飞或者下降等  全部清除!!!
	//js中的计时器 都是有自己的编号 从1开始
	//我也不知道目前哪个计时器在执行 但是 我能获取最后一个计数器的编号!!
	var lastTimer = setInterval(function(){}, 10);
	//从1开始  到最后一个计时器 全部清除!!!
	for(var i = 1; i <= lastTimer; i++){
		clearInterval(i);
	}
	//显示分数板
	endEl.style.display = "block";
	endEl.style.zIndex = 10;
	currentScoreEL.innerHTML = num;//num是全局变量
	//游戏结束 屏幕的点击事件也结束
	rootEl.onclick = null;
}

//---------------------------------------------
//屏幕的点击事件!!!! 注意root太大了 封面盖不住全部的root
//这里不能给root直接设置点击事件   会导致游戏按钮还没点 就已经开始游戏啦
//rootEl.onclick = function(){  这样写有bug
function clickRoot(){
	//每点击一下  播放点击音效
	bulletMusic.play();
	//每点击一下屏幕 需要让小鸟上飞
	//那么此时无论小鸟是哪种飞翔的姿态  都需要重新向上飞
	clearInterval(birdDownTimer);
	clearInterval(birdUpTimer);
	//同一时刻  只能有一个计时器!!
	//上飞的是初始速度
	speed = 10;
	//调用上飞的计时器
	birdUpTimer = setInterval(birdUp, 20);
}

//小鸟上升函数  封装----------
function birdUp(){
	birdImg.src = "img/up_bird.png";
	//注意往上飞 刚开始快  然后会变慢  变速动画!!
	speed -= 0.5;
	if(speed < 0){
		//清除上飞的计时器 开始往下坠
		speed = 0;
		clearInterval(birdUpTimer);
		birdDownTimer = setInterval(birdDown, 20);
	}
	//-----------------------
	birdImg.style.top = birdImg.offsetTop - speed + "px";
	//判断是否到达了顶部  小鸟图片的top值  最小是0
	if(birdImg.offsetTop <= 0){
		//游戏结束
		gameOver();
	}
}

//---------
//碰撞检测!!  参数1就是小鸟  参数2就是上管道 或者下管道
//需要注意  管道外面包着li  所有有效的距左left值   是应该取li的left值! 我们做管道动画移动也是修改了 li的left值进行动画的! 管道相对li的left值始终都是0!
function crash(div1, div2){
		var xLeft = div2.offsetParent.offsetLeft - div1.offsetWidth;
		var xRight = div2.offsetParent.offsetLeft + div2.offsetWidth;
		
		var yTop = div2.offsetTop - div1.offsetHeight;
		var yBottom = div2.offsetTop + div2.offsetHeight;
		//只要div1 在这4个临界值内 那么就说明发生了碰撞
		 if(div1.offsetLeft >= xLeft && div1.offsetLeft <= xRight && div1.offsetTop >= yTop && div1.offsetTop <= yBottom){
		 	//如果发生了碰撞   游戏结束
		 	gameOver();
		 }	
	}
	
	

```
代码仅供学习参考