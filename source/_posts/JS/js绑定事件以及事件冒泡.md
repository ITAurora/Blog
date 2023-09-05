---
title: js绑定事件以及事件冒泡
date: 2020-12-01 11:10:10
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
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			#one{
				width: 400px;
				height: 400px;
				background-color: sandybrown;
			}	
			#two{
				width: 300px;
				height: 300px;
				background-color: yellowgreen;
			}	
			#three{
				width: 200px;
				height: 200px;
				background-color: skyblue;
			}	
		</style>
	</head>
	<body>
		<div id="one">
			<div id="two">
				<div id="three"></div>
			</div>
		</div>
	</body>
</html>
<script type="text/javascript">
	//1.给标签添加点击事件!
//	one.onclick = function(){};    常用且好理解又好记的方式!!
	
	
	//2.通过事件监听的方式  给一个标签绑定事件!!最终结果跟方式1是一样一样的!!!
	//参数1: 事件的类型, 注意不要带on    事件名本来就不带on
	//参数2: 事件发生后会执行的函数
	/*参数3: 是事件冒泡时执行还是事件检测时执行
	 默认不写,值是false 也就是事件冒泡才会执行! 一般都不写!!!
	 如果设置为true,也就是事件检测的时候执行!!!
	 
	 */
	/*
	one.addEventListener("click", function(){
		console.log("one被点击了!!!");
	});
	
	one.addEventListener("mouseenter", function(){
		console.log("鼠标进入了one");
		
	});
	
	*/
	
	
//	one.onclick = function(){
//		console.log("one被点击啦!!");
//	}
//鼠标右键  contextmenu
	one.addEventListener("contextmenu", function(){
		console.log("one被点击了!!!");
		//取消鼠标默认事件样式
		event.preventDefault();
	}, false);
	
	
	two.addEventListener("click", function(){
		console.log("two被点击了!!!");
		//阻止冒泡
//		event.cancelBubble = true;
	}, false);
	
	three.addEventListener("click", function(){
		console.log("three被点击了!!");
		//阻止冒泡
//		event.stopPropagation();
	}, false);
	
	//如果子标签的事件父标签的(记住是事件类型一致-----事件类型一致----------,一旦触发子标签的事件,父标签事件也会被触发!这就是事件冒泡!!
	//只要阻止冒泡,标签事件向上传递就不会再触发父标签中同种类型的事件!!!
	
	/*
	 * 事件的执行过程
	 * 1.事件检测:从浏览器窗口window对象一层一层向下检测,一直到在页面上检测上此标签,就是事件的检测过程!
	 * 
	 * 2.事件冒泡:就是从被点击的标签开始向上进行事件传递.一层一层传递给浏览器进行响应!!!
	 * 
	 * 
	 */
	
	
	
</script>

```
![](https://img-blog.csdnimg.cn/1f3c00a41230483ba6825fe2ae59ce98.png)
