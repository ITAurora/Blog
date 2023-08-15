---
title: 前端js中function构造一般函数
date: 2020-11-10 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/5.jpg
banner_img: ../articleImages/5.jpg
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
	/*函数：具有特定功能的代码块
	 function 函数名 (参数){
	 	
	 }
	 
	 函数分为两大类：
	 1.库函数
	 2.自定义函数
	 */
	//方式1
	function say(){
		document.write("宝贝儿<br />");
	}
	say();
	say();
	say();
	//方式2 a是参数
	//a的位置是形参 
	function print(a){
		document.write("执行了函数print<br />");
		document.write(a);
	}
	//调用时实参传给形参
	 print(666+"<br />");
	 //方式3 
	 function sum(a,b,c){
		document.write("执行了函数sum<br />");
		document.write(a+b+c+"<br />");
	}
	  //js是弱类型语言 并不能指定传参类型
	 sum(1,2,3);
	 sum(1,"spring",3);
	 //对于纯数字少参为number+undefined=NaN
	 sum(1,2);//不写参数默认undefined
	 //方式4 有返回值
	 function buyMilk1(){
	 	document.write("执行了函数buyMilk1<br />");
		var a=1;
		return a;
	}
	 document.write(buyMilk1()+"<br />");
	 function buyMilk2(){
	 	document.write("执行了函数buyMilk2<br />");
		var a=1;
		var b=2;
		return [a,b];
	}
	 document.write(buyMilk2()+"<br />");
	 var n=buyMilk2();
	 document.write(n+"<br />");
	 //带参的函数的返回值  return以下的代码不会继续执行
	 //-------------注意return带回的是参数的值不是参数名-----------
	 function buyMilk3(a,b,c){
	 	document.write("执行了函数buyMilk3<br />");
		return a+b+c;
	}
	 document.write(buyMilk3(1,2,3)+"<br />");
	 var n=buyMilk3(1,2,3);
	 document.write(n+"<br />");
	 //练习 定义函数获取两个数最大值并返回
	 function max(a,b){
	 	document.write("执行了函数max<br />");
	 	return a>b?a:b;;
	 }
	document.write(max(1,2)+"<br />");
	//练习:获取一个数的全部约数
	 function math(a){
	 	document.write("执行了函数math<br />");
	 	for(var i=1;i<=a;i++){
	 		if(a%i==0){
	 			document.write(i+" ");
	 		}
	 	}
	 }
	math(24);
	document.write("<br />");
	//练习:定义函数用于获取一个数组中的最大数
	function max(a){
	 	document.write("执行了函数max<br />");
	 	for(var i=0;i<a.length;i++){
	 		if(i==0){
	 			var max=a[i];
	 		}
	 		if(max<a[i]){
	 			max=a[i];
	 		}
	 	}
	 	return max;
	 }
	var b=[1,2,3,4,6,,19,7,9]
	document.write(max(b)+"<br />");
	document.write(max([1,2,3,4,11,7,9]));
</script>

```
运行结果:
![](https://img-blog.csdnimg.cn/45995865b57342f59347ec365ae1253a.png)
