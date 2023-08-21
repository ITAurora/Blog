---
title: 前端js实现连连看游戏
date: 2020-11-16 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/15.jpg
banner_img: ../articleImages/15.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			ul{
				width: 400px;
				height: 400px;
				border: 1px solid goldenrod;
				margin: 30px auto;
				list-style: none;
				display: flex;
				flex-wrap: wrap;
				justify-content: space-between;
			}
			li{
				width: 100px;
				height: 100px;
				border: 1px solid goldenrod;
				text-align: center;
				line-height: 100px;
				font-size: 30px;
				/*怪异盒模型*/
				box-sizing: border-box;
			}
			
			
		</style>
		<title></title>
	</head>
	<body>
		
		<ul>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
		</ul>
		
		
		
		
		
		
	</body>
</html>

<script type="text/javascript">
	//1.获取标签
	var liArray = document.getElementsByTagName("li");
	
	//2.定义变量
	var numArray = [];
	
	
	
	//3.封装函数
	//随机数
	function randomNum(min, max){
		return Math.floor(Math.random() * (max - min + 1) + min);
	}
	//随机颜色
	function randomColor(){
		var red = randomNum(0, 255);
		var green = randomNum(0, 255);
		var blue = randomNum(0, 255);
		return "rgb(" + red + "," + green + "," + blue + ")";
	}
	
	//封装函数 用于填满数组
	function setNumberArray(){
		//16个数 两两相等
		for(var i = 0; i < 8; i++){
			var temp = randomNum(30, 90);
			//卡着!!一旦随机数已经出现过!就重新再取数字!
			//标记  查看是否可用
			var isExits = false;//默认希望temp不存在
			//经过for循环遍历对比
			for(var j = 0; j < numArray.length; j++){
				if(temp == numArray[j]){
					//随机数已经出现过了!
					isExits = true;
					break;//结束 for..j循环
				}
			}
			//for..j结束  查看isExits的标记状态
			if(isExits == false){
				//随机数可用
				numArray.push(temp);
				numArray.push(temp);
			}else{
				i--; //此次循环失效!i-- 再来一次!!
			}
			
			
		}
		//循环结束   16个数字已经进入数组中
		console.log(numArray);
		//打乱数组	
		crash(numArray);
		console.log(numArray);

		
	}
	//调用函数
	setNumberArray();
	//封装打乱数组的函数
	function crash(arr){
		for(var i = 0; i < 15; i++){
			var n1 = randomNum(0, 15);
			//16个元素,下标是0---15
			var n2 = randomNum(0, 15);
			if(n1 != n2){
				var t = arr[n1];
				arr[n1] = arr[n2];
				arr[n2] = t;
			}	
		}
		
	}
	
	//封装函数 用于设置li标签
	function setLiArray(){
		for(var i = 0; i < liArray.length; i++){
			//赋值文本  li的个数和数字个数一致! 所以下标也一致!
			liArray[i].innerHTML = numArray[i];
			//设置字体颜色随机
			liArray[i].style.color = randomColor();
			//设置li的背景颜色
			liArray[i].style.backgroundColor = randomColor();
		}
	}
	//调用函数
	setLiArray();
	
	//--------------------------------
	//给li添加点击事件
	//专门定义一个数组  来存储点击的li标签
	var arr = [];
	for(var i = 0; i < liArray.length; i++){
		liArray[i].onclick = function(){
			arr.push(this);
			console.log(arr);
		
		//两个就得判断
		if(arr.length == 2){
			//不能重复点击一个标签且点击的两个标签值还得一样
			if(arr[0] != arr[1] && arr[0].innerHTML == arr[1].innerHTML){
				//消除成功!
				arr[0].style.visibility = "hidden";
				arr[1].style.visibility = "hidden";
			}
			
			//在这里  只要arr中存储了两个li  就清空  为下次存储li做准备
			arr = [];
		}
		}
	}
	
	
	
	
</script>

```
运行结果：
![](https://img-blog.csdnimg.cn/dc584f6d60d04ee6b4824c38f26fcc9b.png)
点两个数字相同的棋子：
![](https://img-blog.csdnimg.cn/a7ad3030982e4973889b83c460d50980.png)
