---
title: js的ES6新数组方法
date: 2020-11-27 12:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/6.jpg
banner_img: ../articleImages/6.jpg
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
	
   var arr1=[100,200,300,400,500];
    // forEach() 返回值是undefined  遍历数组
	 var a=arr1.forEach(function(value, index){
		console.log(index , value);
	});
	console.log(a);
	//------------------------------------------------------------
	//map是返回新数组  并且不影响原数组 也是遍历数组
	var a1 = arr1.map(function(value, index){
		console.log(index, value);
		if(value >= 300){
		return value;
		}
	});
	//a1就是新的数组  新数组和原数组 的 元素个数一致!!
	console.log(a1);
	//------------------------------------------------------
	//比map再高级一点 就是过滤filter  也能遍历数组
	var numArray = [2, 3, 4, 5];
	
	var newNumArray = numArray.filter(function(value, index){
		console.log(index, value);
		if(value > 4){
			return value;
		}
	});
	console.log(newNumArray);
	//----------------------------------
	//some() 一边遍历 一边找元素  符合条件就停止遍历查找并且返回true  都不符合就返回false
	var s = numArray.some(function(value, index){
		console.log(index, value);
		return value == 2; //只要这里为true  遍历会直接结束!!!!!
	})
	console.log(s);
	
	//reduce() 聚合函数  返回值就是运算结果
	var result = numArray.reduce(function(sum, value){
		return  sum += value;
	}, 0);
	//参数2的100 就是 sum的初始值!!!!!!!!!!
	console.log(result);
</script>

```
运行结果:
![](https://img-blog.csdnimg.cn/0842a176dedc494aa4fde40dcc7743fd.png)
