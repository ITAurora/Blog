---
title: 利用js写一个简单的接金币小游戏(要用到碰撞检测)
date: 2020-12-15 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/7.jpg
banner_img: ../articleImages/7.jpg
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
			*{
				margin: 0;
				padding: 0;
				-webkit-user-select: none;
			}
			html, body{
				width: 100%;
				height: 100%;
				overflow: hidden;
			}
			/*金币 需要们js动态创建*/
			.jin{
				position: absolute;
				top: -70px;
				width: 70px;
				height: 70px;
			}
			
			#pen{
				width: 103px;
				background: url(img/pen.png);
				height: 48px;
			    position: absolute;
			    left: 0;
			    bottom: 0;
			}
			#score{
				width: 100px;
				height: 100px;
				color: gold;
				font-size: 80px;
				font-weight: bold;
				position: absolute;
				left: 40px;
				top: 40px;
			}
			
			
		</style>
	</head>
	<body>
		<!--分数-->
		<div id="score">0</div>
		<!--盆-->
		<div id="pen"></div>
		
	</body>
</html>
<script type="text/javascript">
	//定义变量 记录分数
	var count = 0;
	

	//实现pen的拖拽事件
	pen.onmousedown = function(){
		//其实不需要考虑 top值 因为只能左右滑动
		var x = event.offsetX; 
		//给屏幕添加鼠标移动事件
		document.onmousemove = function(){
			pen.style.left = event.clientX - x + "px";
		}
		
	}
	
	//鼠标从pen抬起 就是取消移动事件
	pen.onmouseup = function(){
		document.onmousemove = null;
	}
	//给文档也加一个 
	document.onmouseup = function(){
		document.onmousemove = null;
	}
	
	//-------------------------------------------
	//封装产生金币的方法
	function createJin(){
		var jinbi = document.createElement("img");
		jinbi.className = "jin";
		jinbi.src = "img/jin.png";
		document.body.appendChild(jinbi);
		
		//注意 金币的top值都是-70  但是left值需要随机   left值最小是0;最大是屏幕-金币
		jinbi.style.left = Math.floor(Math.random() * (document.body.clientWidth - jinbi.offsetWidth)) + "px";
		
		//金币掉落  计时器动画
		setInterval(function(){
			jinbi.style.top = jinbi.offsetTop + 2 + "px";
			//判断  金币落地 就说明没接住  就删除
			if(jinbi.offsetTop > document.body.clientHeight - jinbi.offsetHeight){
				document.body.removeChild(jinbi);
			}
			//一边下降 一遍判断碰撞检测
			if(crashJin(pen, jinbi)){
				count++;//分数自增
				score.innerHTML = count;
				document.body.removeChild(jinbi);//接住金币 加分  直接删掉金币即可!
			}
		},10);
		
		
		
	}
	//注意 !!!!!!!!
	//再写计时器 每隔0.5秒 创建一个金币
	setInterval(createJin, 800);
	
	//------------
	//封装碰撞检测的方法
	function crashJin(obj1, obj2){
		var xLeft = obj1.offsetLeft - obj2.offsetWidth;
		var xRight = obj1.offsetLeft + obj1.offsetWidth;
		var yTop = obj1.offsetTop - obj2.offsetHeight;
		
		if(obj2.offsetLeft >= xLeft && obj2.offsetLeft <= xRight && obj2.offsetTop >= yTop){
			return true;
		}else{
			return false;
		}	
	}
	
</script>

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/cceac097eb16429ea66652e42d04de0c.png)
