---
title: js中弹窗相关的方法和区别
date: 2020-11-26 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/2.jpg
banner_img: ../articleImages/2.jpg
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
		
		<input type="text" placeholder="请输入文字"/>
		<input type="button" value="失去焦点" id="b"/>
		<input type="button" value="获取焦点" id="f"/>
		<!--弹框-->
		<input type="button"  value="alter" id="a"/>
	</body>
</html>
<script type="text/javascript">
	var input1 = document.querySelector("input");
  
  //获取焦点
	f.onclick = function(){
	  input1.focus();
	}
	//失去焦点
	b.onclick = function(){
		input1.blur();
	}
	
	//-----------
	//弹框 alter()
	a.onclick = function(){
//		window.alert("哈哈哈哈哈");
		//也是弹框   但是是带有疑问的  并且带有布尔返回值
//		var r = confirm("你是帅哥吗?");
//		console.log(r);
        //可以输入的提示框
        var s = prompt("请输猜你喜欢的颜色");
        console.log(s);
       
	}
	
	
</script>

```
