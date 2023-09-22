---
title: js中继承的使用
date: 2020-12-18 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/11.jpg
banner_img: ../articleImages/11.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>

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
	//重点明白  普通继承即可!  apply()  call()
	//至于原型继承,了解即可!可先忽略!!
	function Person(name, sex, age, phone, ID){
		this.name = name;
		this.sex = sex;
		this.age = age;
		this.phone = phone;
		this.ID = ID;
		this.sleep = function(){
			console.log("睡觉!")
		};
		this.eat = function(){
			console.log("吃饭!");
		}
		
		
		
	}
	var p1 = new Person("狗子", "男", 19, "1498098344", "410203890839083");
	console.log(p1);
	p1.eat();
	p1.sleep();
	//给原型对象添加一个方法
	Person.prototype.shopping = function(){
		console.log("陪女朋友逛逛街啦!");
	}
	p1.shopping();
	//给原型对象添加一个属性  
	Person.prototype.address = "地球村";
	console.log(p1.address);
	//--------------------------------------------
	function Student(num, name, sex, age, phone, ID, score){
		//来!!继承关系!! 可以继承Person 顺便用一用父类的构造函数给属性赋值
		Person.apply(this, [name, sex, age,phone, ID]);

		this.num = num;
		this.score = score;
		//新增方法
		this.study = function(){
			console.log("学生嘛!好好的学习,为了更好的生活!");
		}
	}
	
		//原型不能直接继承
	//原型继承---------------------------------
	var F = function(){};
	F.prototype = Person.prototype;
	Student.prototype = new F();
	Student.prototype.constructor = Student;
	//constructor 中文--叫做构造函数
	//constructor原型对象自身的属性,默认执行原型对象所引用的构造函数!!
	
	
	//创建学生对象
	var stu = new Student(1, "鹏鹏", "男", 19, "1782987373", "412903893790379", 99);
	console.log(stu);
	stu.sleep(); //子类调用父类的方法
	stu.eat();//子类调用父类的方法
	stu.study();//子类调用自己本类中的新增方法
	stu.shopping();//调用父类中的原型方法!!!

	//------------------------------------------------------
	//练习:定义teacher教师类  继承子Person
	function Teacher(num, name, sex, age, phone, ID, job){
		Person.call(this, name, sex, age, phone, ID);
		this.num = num;
		this.job = job;
		this.shangban = function(){
			console.log("好好上班!");
		}
		
	}
	var F = function(){};
	F.prototype = Person.prototype;
	Teacher.prototype = new F();
	Teacher.prototype.constructor = Teacher;
	
	
	
	//类名  == 构造函数名
	var t1 = new Teacher("56", "姣姣啊", "女", 18, "18638520107", "4102937983739873", "前端讲师");
	console.log(t1);
	console.log(t1.name);
	t1.name = "Aurora";
	t1.sleep();
	t1.eat();
	t1.shangban();
	t1.shopping();
	//call(this, 参数1, 参数2, 参数3....)
	//apply(this, [参数1, 参数2, 参数3..])
	//最终实现的效果都是一样的!!都是为了继承!!!
	//-----------------------------------------------------------------
	
	
	
	//注意:想要调用父类原型中的方法!!必须要先继承原型! 再创建子类对象!!!
	var s1 = new Student();
	s1.shopping();
	
	
</script>
<!--
	1.子类继承父类,就会继承父类的属性he方法!!
	2.子类还可以新增属性和方法!!
	3.继承是单向!!!
	
-->
```
![](https://img-blog.csdnimg.cn/a0c9dc3b6c3a490ea63496be57953167.png)
