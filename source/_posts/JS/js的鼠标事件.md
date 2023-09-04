---
title: js的鼠标事件
date: 2020-11-30 10:10:10
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
		<meta charset="utf-8" />
		<title></title>
		<style type="text/css">
			div{
				width: 300px;
				height: 300px;
				background-color: skyblue;
			}
		</style>
	</head>
	<body>
		<input type="button" value="单击事件" id="i1"/>
		<input type="button" value="双击事件" id="i2"/>
		<input type="button" value="按钮按下事件" id="i3"/>
		<input type="button" value="鼠标右键" id="i4"/>
		<input type="button" value="鼠标按钮抬起事件" id="i5"/>
		<div id="div1">模拟鼠标进出以及鼠标移动事件</div>
	</body>
</html>
<script type="text/javascript">
	/*
	 * js是一个以事件为驱动的脚本语言 在开发过程中想要实现交互就要借助事件完成
	 * 注意!!!!!!!!!!!!!!!!!
	 * 系统为每一个事件创建一个事件对象event 事件对象中存储着所有与用户交互的
相关信息 可以通过event对象获取对应的某些数据 从而进行逻辑操作
	 * 
	 */
	//单击事件
	i1.onclick=function(){
		//重点!!!每个事件都有事件对象event
		//兼容浏览器的写法 (主要为了兼容火狐浏览器 火狐会把事件对象传递给参数)
		var ev=event||e;
		console.log(ev);
		console.log("单击事件");
	}
	//双击事件
	i2.ondblclick=function(){
		console.log(event);
		console.log("双击事件");
	}
	//鼠标按钮按下事件
	i3.onmousedown=function(){
		console.log("鼠标按钮按下");
	}
	//鼠标按钮抬起事件
	i5.onmouseup=function(){
		console.log("鼠标按钮抬起");
	}
	//鼠标右键
	i4.oncontextmenu=function(){
		console.log("鼠标右键");
	}
	//鼠标区域事件
//	div1.onmouseenter=function(){
//		console.log("鼠标进入")
//	}
	div1.onmousemove=function(){
		console.log("鼠标移动")
	}
//	div1.onmouseleave=function(){
//		console.log("鼠标离开")
//	}
	//enter和leave 不存在事件冒泡
	//over和out 存在事件冒泡
	div1.onmouseover=function(){
		console.log("over鼠标进入")
	}
	div1.onmouseout=function(){
		console.log("out鼠标离开")
	}
	//滚轮滚动事件
	div1.onmousewheel=function(){
		console.log("滚轮滚动");
	}
	//鼠标事件    鼠标按下事件
	div1.onmousedown=function(){
		console.log(event.button);
		if(event.button==0){
			console.log("左键");
		}
		if(event.button==1){
			console.log("滚轮键");
		}
		if(event.button==2){
			console.log("右键");
		}
	}
</script>
```
![](https://img-blog.csdnimg.cn/6c7656128f154389beecc391ce1d0be3.png)
