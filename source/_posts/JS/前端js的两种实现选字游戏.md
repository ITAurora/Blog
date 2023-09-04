---
title: 前端js的两种实现选字游戏
date: 2020-11-14 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/14.jpg
banner_img: ../articleImages/14.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			.root{
				width:350px;
				height: 450px;
				border: solid 2px red;
				margin: 20px auto;
				font-size: 22px;
				font-weight: bold;
				cursor: pointer;
				
			}
			.time{
				float: left;
				
			}
			.score{
				float: right;
				
			}
			.big-text{
				/*background-color: pink;*/
				width: 100%;
				text-align: center;
				font-size: 200px;
			}
			.small-text{
				list-style: none;
				width: 100%;
				height: 40px;
				display: flex;
				justify-content: space-around;
				/*background-color: salmon;*/
				padding-top: 50px;
				font-size: 32px;
			}
		</style>
	</head>
	<body>
		<div class="root">
			<span class="time">剩余时间:15</span>
			<span class="score">分数:0</span>
			<p class="big-text">红</p>
			<ul class="small-text">
				<li>红</li>
				<li>黄</li>
				<li>蓝</li>
				<li>绿</li>
				<li>紫</li>
			</ul>
		</div>
	</body>
</html>
<script type="text/javascript">
	//获取标签
	var scoreEl=document.getElementsByClassName("score")[0]
	var timeEl=document.getElementsByClassName("time")[0];
	var bigEl=document.getElementsByClassName("big-text")[0];
	var smallArray=document.getElementsByTagName("li");
	//定义变量
	var score=0;
	var time=15;//默认时间
	//重点
	var textArray=["红","黄","蓝","绿","紫"];
	var colorArray=["red","yellow","blue","green","purple"];
	//定义变量 存储答案
	var daan;
	//封装函数
	//随机函数
	function randomNum(min,max){
		return Math.floor(Math.random()*(max-min+1)+min);
	}
	//处理大字
	function changeBigText(){
		//随机文字
		var index=randomNum(0,textArray.length-1);
		bigEl.innerHTML=textArray[index];
		//随机颜色
		var colorIndex=randomNum(0,colorArray.length-1);
		bigEl.style.color=colorArray[colorIndex];
		//答案接收
		daan=colorArray[colorIndex];
	}
	//调用处理大字的方法
	changeBigText();
	//----------------处理小字------------
	function changeSmallText(){
		//打乱文字数组
		crashArray(textArray);
		//打乱颜色数组
		crashArray(colorArray);
		//打乱之后再给li赋值
		for(var i=0;i<smallArray.length;i++){
			smallArray[i].innerHTML=textArray[i];
			smallArray[i].style.color=colorArray[i];
		}
		
	}
	//调用改变小字的函数
	changeSmallText();
	//打乱数组
	function crashArray(arr){
		for(var i=0;i<10;i++){
			var n1=randomNum(0,4);
			var n2=randomNum(0,4);
			if(n1!=n2){
				var t=arr[n1];
				arr[n1]=arr[n2];
				arr[n2]=t;
			}
		}
	}
	//-------------------------添加点击事件和判断
	for(var i=0;i<5;i++){
		smallArray[i].onclick=function(){
			console.log(getColorByText(this.innerHTML));
			var color=getColorByText(this.innerHTML);
			//与答案对比
			if (color == daan) {
				//加分 并刷新大小字
				score++;
				changeBigText();
				changeSmallText();
				//将分值赋值给分数标签
				scoreEl.innerHTML="分数"+score;
			}
		}
	}
	//处理点击的中文汉字 获取其对应的英文单词
	function getColorByText(text){
		switch(text){
			case "红":
			return "red";
			case"黄":
			return "yellow";
			case"蓝":
			return "blue";
			case"绿":
			return "green";
			case"紫":
			return "purple";
			default:
			break;
		}
	}
	
	//------------------------计时器
	var s1=setInterval(function(){
		time--;
		if (time==0) {
			//清除计时器
			clearInterval(s1);
			//关闭点击事件
			for(var i=0;i<smallArray.length;i++){
				smallArray[i].onclick=null;
			}
		}
		timeEl.innerHTML="剩余时间:"+time;
	},1000);
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/16f216f6d1c8440b91a3f3bae521242f.png)
简单的实现,感觉代码比较经典就记了下来

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style>
    *{
        margin: 0;
        padding: 0;
    }
    .root{
        width: 180px;
        height: 250px;
        margin: 100px auto;
        border: 1px solid black;
        position: relative;
    }
    .root div{
        font-size: 130px;
        text-align: center;
        width: 100%;
    }
    .root ul{
        position: absolute;
        bottom: 10px;
        left: 0;
        list-style: none;
        display: flex;
        width: 100%;
        justify-content: space-around;
        font-size: 20px;
    }
</style>
<body>
    <div class="root">
        <div style="color: blue;">红</div>
        <ul>
            <li style="color: purple;">红</li>
            <li style="color:green">绿</li>
            <li style="color: blue;">蓝</li>
            <li style="color:red">黄</li>
            <li style="color:yellow">紫</li>
        </ul>
    </div>
</body>
</html>
<script>
    var div1=document.getElementsByTagName("div")[1];
    var liArray=document.getElementsByTagName("li");
    var arr1=["红","绿","蓝","黄","紫"];
    var arr2=["red","green","blue","yellow","purple"];
    for(i=0;i<liArray.length;i++){
        // 来保存下标
        liArray[i].sum=i;
        liArray[i].onclick=function(){
            var color1=div1.style.color;
            console.log(color1);
            var color2=arr2[this.sum];
            console.log(color2);
            if(color1==color2){
                div1.innerText=arr1[Math.floor(Math.random()*5)];
                div1.style.color=arr2[Math.floor(Math.random()*5)];
            }else{
                alert("再试试！")
            }
        }
    }
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/6d862275b7704f92a55b84d97b9a2a30.png)
