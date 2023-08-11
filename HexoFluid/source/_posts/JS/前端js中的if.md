---
title: 前端js中的if
date: 2020-11-04 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/13.jpg
banner_img: ../articleImages/13.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```js
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
	 代码的执行顺序:
	 1.顺序结构,从上倒下顺序执行!
	 2.分支结构,按照条件选择性的执行某一段代码
	 3.循环结构,在符合条件下重复多次执行一段代码
	 */
	
	//if分支结构 方式1:--------------------------------
	if(false){
		//只有条件为真  才会执行!
		console.log("哈哈哈");
	}
	var age = 18;
	if(age >= 18){
		console.log("欢迎来自德玛西亚的钻石王者....");
	}
	//if分支结构  方式2:--------------------------------
	if(age >= 18){
		console.log("来玩呀!!");
	}else{
		console.log("哪凉快哪去!!");
	}
	
	//------------
	//计算闰平年
	//闰年:年份对4整除但是不对100整除.或者年份对400整除!
	var year = 1900;
	if((year % 4 == 0 && year % 100 != 0) || year % 400 == 0){
		console.log(year + "是闰年");
	}else{
		console.log(year + "是平年");
	}
	//if分支结构   方式3----------------------------
	var score = 89;
	if (score >= 90) {
		console.log("秀儿");
	}else if(80 <= score ){
		console.log("不错!");
	}else if(60 <= score){
		console.log("勉强及格!")
	}else{
		console.log("凉凉!");
	}
	//  80 < score < 90 不可以
	// 80 < score && score < 90
	
	
	//坑1-------------------------------
	score = 59;
	if(score > 60)
	console.log("及格啦!"); //只对第一行代码起作用
	console.log("真开心");//根本就不在if分支中
	//坑2-------------------------
	score = 78;
	if(score > 80);{
		console.log("呵呵呵呵");
	} //此时{} 跟if没有关系!!
	//  ;分号  就是一句话的结束! 
	
	
	
</script>

```
运行结果:
![](https://img-blog.csdnimg.cn/b05ca1ce077a439cbb4c00f2bc7424bf.png)
