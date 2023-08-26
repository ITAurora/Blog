---
title: 利用js写一个根据高度插入的瀑布流
date: 2020-11-21 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/12.jpg
banner_img: ../articleImages/12.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>瀑布流</title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			
			ul{
				list-style: none;
			}
			.root{
				width: 1000px;
				border: 2px solid gold;
				/*高度需要根据随机不断变化 */
				margin: 30px auto;
				overflow: hidden;
				/*弹性布局  有坑!!!*/
				/*display: flex;
				justify-content: space-around;*/
			}
			.root ul{
				width: 240px;
				border: 1px solid seagreen;
				float: left;
				color: white;
				margin: 4px;
				text-align: center;
				font-size: 90px;
			}
		</style>
	</head>
	<body>
		<!--底部的div-->
		<div class="root">
			<ul></ul>
			<ul></ul>
			<ul></ul>
			<ul></ul>
		</div>
	</body>
</html>
<script type="text/javascript">
	
	//1.获取标签
	var ulArray = document.querySelectorAll("ul");
	//2.定义变量
	
	//3.函数
	//封装随机数
	function randomNum(min, max){
		return Math.floor(Math.random() * (max - min + 1) + min);
	}
	//封装随机背景色
	function randomColor(){
		var red = randomNum(0, 255);
		var green = randomNum(0, 255);
		var blue = randomNum(0, 255);
		return "rgb("+ red + "," + green + "," + blue + ")";
	}
	
	//循环50次  准备创建50个li
	for(var i = 0; i < 50; i++){
		var li = document.createElement("li");
		li.innerHTML = i + 1;
		li.style.backgroundColor = randomColor();
		//随机一个高度
		var height = randomNum(100, 500);
		li.style.lineHeight = height + "px";
		li.style.height = height + "px";
		//想想办法!!看哪个ul高度最小!! 谁最矮  就把新建的li放在哪个ul中!!
		//定义变量    每次循环都假设下标0的ul 最矮!!
		var index = 0; //用来记录最矮的ul的下标!!!
		//循环遍历 4个ul  下标0--3
		for(var j = 1; j < ulArray.length; j++){
			if(ulArray[index].offsetHeight > ulArray[j].offsetHeight){
				index = j;
			}
		}
		//index 就记录着 最矮的 ul的下标!!　类似10个随机数,找最大最小值以及位置
		ulArray[index].appendChild(li);
		
	}
	
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/5e04d14fc1b84ce796f2da66564b4606.png)
