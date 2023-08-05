---
title: 前端js变量
date: 2020-03-20 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/7.jpg
banner_img: ../articleImages/7.jpg
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
	//1.变量  在程序运行期间,值可以发生变化的量叫做变量.
	var a = 10; //number
	//但是浏览器在解析代码的时候  会自动帮我们区分类型
	//注意 变量的类型由赋的值来决定  typeof 变量名; 可查看变量类型
	console.log(typeof a);
	a = "哈哈"; //string
	console.log(typeof a);
	a = 89.789; //number     整数 小数都是number
	console.log(typeof a);
	var a = "a"; //string   ""   ''  单双引号都是string
	console.log(a);
	var name = "Aurora";
	var isGirl = true;    //boolean 布尔真假类型  非假即真  true false
	console.log(typeof isGirl)
	var sex;       //只声明变量 不赋值 就是undefined
	console.log(sex, typeof sex);
	//修饰一个学生
	//对象
	var student = {
		name:"王二狗子",
		sex:"男",
		age:18
	};             //对象  object
	console.log(student, typeof student);
	//特殊的number
	var n = 10;
	var m = "你好";
	var l = n - m; //不合法运算  NaN
	console.log(l, typeof l);
</script>



<!--
	1.js的历史
	2.js的组成
	a. ECMAScript,指代javascript的一些基础语法规则,例如变量.语句执行顺序,函数,对象等
	b.DOM(document object model)文档对象模型,完成对文档中的元素进行增删改查.
	c.BOM(browser object model)浏览器对象模型(数据存储在浏览器中,都是通过window调用的)
	d.事件处理  event事件,鼠标,键盘,滚轮,移动端等事件.
	ps:以上也是我们学习js的步骤,大家整理笔记模块就可按照这个进行划分!
	
	3.js语言的特点
	a.弱类型语言
	b.直译型语言
	c.不是完全的面向对象
	d.跨平台性
	e.动态性,基于事件驱动的形式
	
	4.js的引入方式
	a.行间引入 
	b.内部引入
	c.外部引入
	
	变量-------------------
	程序运行期间,值可以发生改变的量.本质就是一块存值空间;
	变量是程序的最小构成单元!很重要!
    1.变量的命名规则
    a.数字 字母 下划线_ $都可用.但是数字不可开头
    b.变量名不要使用系统保留字,例如var  console等
    c.变量名尽量--见名知意
    
    2.语法规则
    var 变量名  = 值;
    =叫做赋值号, 从后往前赋值!   
       例如: var a = 10; 就是整数10赋值给变量a!
    
       数据类型
	1.number类型    整数,小数, 不合法的运算结果NaN
	2.string类型   字符串类型  ""  '' 单双引号都是string
	注意;双引号不能在内部嵌套双引号,可以嵌套单引号;
	" '' "  双内部嵌套单或者  ' "" ' 单内部嵌套双都可!!!
	3.undefined类型   只声明变量,但是没有赋值就是undefined类型!
	4.boolean 布尔,真假  true false
	5.object 对象类型   有很多种形式的变量都是object类型!重点记忆!!
	null 这个叫做空值,也是对象类型!!
	a. var student = {
		属性名:属性值
		...
	};  
	
	
	
-->

```
控制台结果:
![](https://img-blog.csdnimg.cn/04fd78188ec54496837dbfd5486bf48d.png)
