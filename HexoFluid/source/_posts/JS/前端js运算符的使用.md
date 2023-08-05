---
title: 前端js运算符的使用
date: 2020-03-20 12:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/8.jpg
banner_img: ../articleImages/8.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```js
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>运算符</title>
	</head>
	<body>
	</body>
</html>
<script type="text/javascript">
	//算术运算符
	var a = 10, b = 20;
	var c = a + b;
	console.log(c);
	c = a - b;
	c = a / b;
	console.log(c);//除法可有小数点
	//取余,取的是余数  例如:数学中:7除以2=3...1    我们就要余数1
	a = 7;
	b = 2;
	c = b % a;  //2 / 7 = 0 ...2
	console.log(c);
	//-----------------
	//递减-1 和递增  +1
	var num1 = 20;
	num1++;    //等价于 num1 = num1 + 1;
	console.log(num1);
	++num1;
	console.log(num1);
    //注意   ++在前 先自增后执行语句; 如果++在后,就先执行语句再自增!
    console.log(++num1);//????
	a = 10;
	b = 20;
	//a +++ b  是(a++)  + b  ++在后先执行语句,后自增
	c = a++; 
	console.log(a+(++b));
	//----------------------------------
	//隐式转换问题!!!
	// +  既可以加法运算,也可以字符串拼接; 
	var s1 = "哈哈";
	var s2 = "呵呵";
	console.log(s1 + s2); //不会报错,是字符串拼接的结果: 哈哈呵呵
	//但是   字符串+数字类型; 就会自动把数字转为字符串,做拼接!
	var s3 = 1000;
	console.log(s1 + s3);//不会报错,是字符串拼接结果:哈哈1000
	var s4 = s3 + "";
	console.log("s4是----", s4, typeof s4);

	
	//console.log(值1, 值2, 值3..); 通过,逗号分隔 可以同时输出多个值	
	//---------------------------------------
	// - 减法以及(*乘法 /除法  %取余法) 也有隐式转换
	//例如: 字符串数字 - number型数字 就会把字符串数字转为number再运算!
	var s5 = "100"; //注意, 一定要是纯数字字符串才可以转换成功!
	var s6 = 90;
	var s7 = s5 - s6; 
	console.log("s7的值是:" , s7, typeof s7);
	s7 = s5 + s6;
	console.log("加法后s7的值是:" , s7, typeof s7);
	//那么  +数字   -数字   正负转换为number
	s7 = s5 - 0;
	console.log("减0后s7的值是:" , s7, typeof s7);
//----------------------------------------------------------
    //复合运算符  
    //很简单 就是只要符合条件,就可简写
    //例如
    var a = 10, b = 5;
    a = a + b; // a += b; 简写而已  += 不可分开
    a = a - b; // a -= b;
    //注意    a = b - a; 肯定不行  不可用 -=
    a = a / b;   
    //简写  a /= b;    但是a = b / a;肯定是不行的!!
    a = a * b; // a *= b;
    //.....
    a += 1; //就是  a++  就是 a = a + 1;
    b -= a; // b = b - a;
    //-----------------------------------------------------
    //  比较运算符      其结果都是布尔类型  true 和  false
    a = 10;
    b = 20;
    var c = a > b; //肯定是错的  10 > 20就为假 false
    console.log(c);
    c = a < b;//true
    c = a == b;// == 是判断是否相等,不是赋值!!!  false
    console.log(c);
    c = a != b;// != 是判断两个值不相等  10 != 20为真!
    a = "10";
    b = 10; 
    //数字10和字符串10相比较
    console.log("10=='10'", a == b); //true  ==仅仅比较值
    console.log("10==='10'", a === b);// false  ===不仅比较值还 比较类型 
    //-----------------------------------
    //逻辑运算符
    // &&  逻辑与  两边条件同时为真则为真
    // ||  逻辑或  两边条件只有一个为真,就为真
    // !   逻辑非   取反操作  
    var n = 10, m = 5;
    var s = n > 30 && m < 1;
     console.log(s);
     
    s = n < 9 || (m > 3 || 9 > 10);
    console.log(s);
    
     //取反
     console.log(!s);
    //-------------------------------------------------
    //条件运算符  三目运算符 
    //  布尔值  ? 值1 : 值2;
    //如果布尔值为true 就取走值1;  如果布尔值为假  就取走值2
    s = true ? "哈哈" : "呵呵";
    // s的值就是  哈哈
    s = false ? 666 : 999;
    // s的值就是   999
    a = 10;
    b = 50;
    s = a > b ? "a大" : "b大";
    console.log(s);
    s = a > b ? a : b;
    console.log(s);
    
    

    
    
    

	
	
	
</script>







<!--
	运算符
	1.=  赋值号
	2.算术运算符  +   -   *  /(除法)  %(取余)   ++(递增)   --(递减)
	3.复合运算符  +=   -=    *=   /=   %=
	4.比较运算符  >   <   >=   <=  ==(等于)  !=(不等于)  ===(全等于)
	5.逻辑运算符   &&  || !
	6.条件运算符   ?  :
		
	
	
	
	
-->

```
控制台运行结果:
![](https://img-blog.csdnimg.cn/7e95f72967fa404eaec92e9e2480a57c.png)


