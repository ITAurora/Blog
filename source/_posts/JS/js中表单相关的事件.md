---
title: js中表单相关的事件
date: 2020-12-01 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/10.jpg
banner_img: ../articleImages/10.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<form action="" method="get" id="f">
			<input type="text" placeholder="请输入文本" id="i1"/>
			<input type="checkbox" id="i2"/>
			<input type="submit" value="提交"/>
			<input type="reset" value="重置"/>
		</form>
	</body>
</html>

<script type="text/javascript">
	//表单事件仅仅适用于表单操作以及表单类型的控件
	/*  在js中,事假大多都以on..开头
	 onfocus 当某个表单控件处于被选中状态的时候执行(获取焦点)
	 onblur  当某个表单控件取消被选中状态的时候执行(失去焦点)
	 
	 */
	i1.onfocus = function(){
//		console.log("获取焦点!!")
//		console.log(i1.value);
	}
	i2.onfocus = function(){
		console.log("复选框获取焦点!!")
	}
	i1.onblur = function(){
//		console.log("失去焦点!!");
	}
	
	//提交事件和重置事件  都是直接作用于  form 表单的!!!!!!
	//获取提交按钮点击事件
	//注意注意!!!!!!!!!!!!  
	f.onsubmit = function(){
		alert("哈哈哈哈哈哈哈哈哈哈或或");
	}
	
	f.onreset = function(){
		alert("重置按钮!!!");
	}
	//---------------------------
	//onchange 多用于下拉框事件!!!!
	i1.onchange = function(){
		//输入框中的值 跟上次点击的不一样  就会执行此事件!!!
		console.log("值改变啦!!!");
	}
	
</script>
```
![](https://img-blog.csdnimg.cn/54075224136a4727a9539ffc1743cca6.png)
