---
title: 前端js的两种去重算法
date: 2020-11-16 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/16.jpg
banner_img: ../articleImages/16.jpg
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
	</body>
</html>
<script type="text/javascript">
	
//	8个数字  8个不重复的数字
	var numArray = new Array(); // 20---30
	for(var i = 0; i < 8; i++){
		var a =Math.floor(Math.random() * 8 + 20);
		//在放入数组之前  先对比
	    var isExits = false;
	 
	   for(var j = 0; j < numArray.length; j++){
	   	if(a == numArray[j]){
	   		isExits = true;
	   		break;
	   	}
	   }
       //经过for循环对比!!
       if(isExits == true){
		 i--;	
		}else{
			numArray.push(a);
		}
		
	}
	
	console.log(numArray);
//	方法2利用contains方法
	var numArray = []; // 20---30
	for(var i = 0; i < 8; i++){
		var a =Math.floor(Math.random()*8 + 20);
		//在放入数组之前  先对比
	    var isExist = numArray[i].contains(a);
       //经过contains判断是否重复!!
       if(isExist == true){
		 i--;	
		}else{
			numArray.push(a);
		}
		
	}
	console.log(numArray);
	
	
	
</script>

```
contains方法只能在火狐浏览器中实现
呃  但是我没使用成功