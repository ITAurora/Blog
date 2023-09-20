---
title: js中面向对象的使用
date: 2020-12-16 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/9.jpg
banner_img: ../articleImages/9.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
	</head>
	<body>
		
	</body>
</html>
<script type="text/javascript">
	//JavaScript中的对象是拥有属性和方法的集合.
	//方式1:
	var stu = {
		name:"王二狗子",
		sex:"男",
		age:18,
		hobby:["唱", "跳", "rap", "篮球"],
		run:function(){
			console.log("奔跑吧!兄dei");
		}
	};
	
	
	//新增属性
	stu.num = 1;
	stu.study = function(){
		console.log("学习使你快乐!!");
	}
	//调用属性he方法
	console.log(stu.num);
	console.log(stu.name);
	stu.run();
	stu.study();
	console.log(stu);
	//---------------------------------------
	//方式2:
	var obj = new Object();
	obj.name = "王美丽";
	obj.sex = "女";
	obj.eat = function(){
		console.log("请你次饭啊!");
	}
	console.log(obj);
	//----------------------------------------
	//方式3:工厂模式
	/*对象的工厂模式,就是把创建对象封装在函数中; 那么此函数的意义就在于创建对象!!*/
	function person(name, sex, age, phoneNum){
		//把创建对象 封装在函数内  能通过点语法跟在对象后面的 只能是属性
		var p = new Object();
		p.name = name;
		p.sex = sex;
		p.age = age;
		p.phoneNum = phoneNum;
		p.print = function(){
			console.log("我的名字是" + this.name + ",今年" + this.age + "岁,电话是" + this.phoneNum + "欢迎联系我啊!");
		}
		//最关键的一步!!
		return p; //p在函数内部,就是局部变量  想出函数就需要返回值
	}
	var p1 = person("阿峰", "男", "30", "4546456");
	console.log(p1);
	var p2 = person("阿黄", "男", "30", "6456345");
	console.log(p2);
	p1.print();
	p2.print();
	//-----------------------------------------------
	//我们看看系统是怎么创建对象的?
	var obj = new Object();
	var arr = new Array();
	console.log(arr);
	var reg = new RegExp("");
	console.log(reg);
	var str = new String("df");
	console.log(str);	
	var now = new Date();
	//...等 以上都是系统定义好的构造函数,搭配上创建对象的关键字new  来统一创建对象!!
	
	//那如果我想创建一个student类型的对象呢?想创建dog类型的对象呢?.....
	//如果系统没有提供你想要的对象类型,那么就可以模仿系统自定义对象类型!!!!
	//注意!!你看 new后面的就是构造函数!专门用于构造对象!构造函数要求函数名首字母大写!!
	
	//Student类型构造
	function Student(num, name, age, sex){
		//属性
		this.name = name; //this指代将来创建的对象
		this.num = num;
		this.age = age;
		this.sex = sex;
		//方法
		this.run = function(){
			console.log("跑早操!!10圈!");
		}
		this.study = function(){
			console.log("good good study! day day up!");
		}
	}
	//关键字new 搭配构造函数!来创建对象!!
	var s1 = new Student(1, "阿宁", 18, "男");
	console.log(s1.name);
	console.log(s1);
	s1.run();
	s1.study();
	var s2 = new Student(2, "杰克", 18, "男");
	console.log(s2);
	s2.run();
	/*new关键字的作用:
	  当使用new来调用一个构造函数的时候,系统会在函数内部自动创建一个空对象.然后让构造函数中的this指向该对象;经过实参传值给形参,形参赋值给属性等操作之后! 在将此对象作为返回值返回出去!  就类似我们自己封装的工厂模式!只不过创建步骤和返回步骤可省略! 由系统完成!!
	*/
	//练习:定义一个Dog类型对象的构造函数.并且创建对象
	//练习:定义一个Car类型对象的构造函数.并且创建对象!
	
	function Dog(brand, name, color){
		this.brand = brand;
		this.name = name;
		this.color = color;
		this.run = function(){
			console.log(this.name + "撒欢吧!!");
		}
	}
	var dog1 = new Dog("哈士奇", "傻狗", "黑白配");
	console.log(dog1);
	dog1.run();
	var dog2 = new Dog("泰迪", "提莫", "黄不拉几");
	console.log(dog2);
	dog2.run();
	
	
	function Car(brand, color, price){
		this.brand = brand;
		this.color = color;
		this.price = price;
		
	}
	var car1 = new Car("布加迪威龙", "骚红色", 998);
	console.log(car1);
	var car2 = new Car("兰博基尼", "皎月白", 999999);
	console.log(car2);

</script>
 
```
![](https://img-blog.csdnimg.cn/786322b13d474745adb80e8efc1cb10c.png)
