---
title: js中原型的使用
date: 2020-12-17 10:10:10
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
	</body>
</html>
<script type="text/javascript">
	/*
	 原型:js中所有的函数都有一个属性prototype属性! 这属性引用了一个对象,就是原型对象!简称为原型!
	 也就是说这个对象不需要你来创建,只要你有构造函数,那么这个对象就会自动创建好!!
	 作用:允许我们为对象添加新的属性或者方法.多用于系统提供的构造函数,因为系统提供的函数我们是看不到具体的实现.
	 */
	//例如:
	var arr = new Array(); 
	//你看Array() 就是系统提供的构造函数,用于创建数组对象!而且系统还为数组对象提供了很多好用的方法,比如 pop()  push() splice() shift() sort()等等,但是我现在需要一个功能就是对数字类型的数组中的所有元素求和!系统并没有提供此功能!
	//所以,我们就可以使用原型 新增功能!
	//原型的存在就是为了看不见源代码的类,新增一些方法he属性!!!
	Array.prototype.add = function(){
		var sum = 0;
		for(var i = 0; i < this.length;i++){
			sum +=  this[i];
		}
		return sum;
	}
	//将来只要是个数组,就能调用add这个方法!
	var a1 = [289, 37, 100, 200];
	console.log(a1.add());
	var a2 = new Array();
	a2.push(23);
	a2.push(100);
	console.log(a2.add());
	
	//练习:给Date添加一个功能,用于输出中文的周一,周二...
	Date.prototype.getWeek = function(){
		var weekArray = ["周日", "周一", "周二", "周三", "周四", "周五", "周六"];
		return weekArray[this.getDay()];//getDay() 0--6 周日-周六
	}
	//月份 1-12月  0--11
	Date.prototype.getChineseMonth = function(){
		return ["1月", "2月", "3月", "4月", "5月", "6月", "7月", "8月", "9月", "10月", "11月", "12月"][this.getMonth()];
		//方式2
//		return this.getMonth() + 1 + "月";
	}
	var now = new Date();//此时此刻的系统时间
	console.log(now.getWeek());
	console.log(now.getChineseMonth());
	var d1 = new Date(1628374764839);//按照某个时间戳创建日期对象,时间戳就是1970到某个时间的毫秒数
	console.log(d1.getFullYear());
	console.log(d1.getChineseMonth());
	console.log(d1.getWeek());
	//新增方法: 用于输出中国的时间日期格式   xxx年xx月xx日  时:分:秒 周几
	Date.prototype.formatString = function(){
		return this.getFullYear() + "年" + this.getChineseMonth() + this.getDate() + "日 " + this.getHours() + ":" + this.getMinutes() + ":" + this.getSeconds() + " " + this.getWeek();
	}
	
	console.log(now.formatString());
	console.log(d1.formatString());
	
	//-------------------------------------------------
	function Car(color){
		this.color = color;
		
	}
	var c1 = new Car("白色");
	//自定义构造函数 也可以写原型  但是你既然缺少功能 为何不在构造函数中直接写了!!!
	Car.prototype.run = function(){
		console.log("跑起来");
	}
    c1.run();
</script>

```
![](https://img-blog.csdnimg.cn/6814e232487a4dd2be0e387a29c451f7.png)

