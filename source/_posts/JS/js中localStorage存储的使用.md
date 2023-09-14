---
title: js中localStorage存储的使用
date: 2020-12-10 10:10:10
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
		<meta charset="utf-8" />
		<title></title>
	</head>
	<body>
		
	</body>
</html>
<script type="text/javascript">
	/*
	 localStorage本地存储  HTML5的新技术!
	 特点:
	 1.长久存储,没有时间限制
	 2.自带增删改查的函数,特别好用!!
	 3.localStorage 是系统提供的全局对象,直接访问即可!!
	 重要:
	 localStorage不仅做本地存储,以后更多的功能是可以跨页面传值!
	 页面传值,才是它更好用的功能!!!
	 因为浏览器只有一个,所以其存储数据的位置也只有一个!那就意味着无论你从哪个页面将数据存储,它们都是存在同一个对象localStorage中.那么你就能从任意页面将数据取出!!!
	 
	 
	 
	 */
	
//	console.log(localStorage);
	//1.增  就是存储数据
	//写法1  对象.属性
//	localStorage.username = "Aurora";
//	localStorage.passwd = "666";
	//写法2  索引的写法 对象["属性名"]
//	localStorage["age"] = 20;
//	localStorage["phone"] = "15362837489";
	//写法3 localStorage自带的方法
//	localStorage.setItem("sex", "女");
//	localStorage.setItem("hobby", ["唱", "跳", "rap"]);
	
	//2.修改 跟增数据一样直接访问属性即可
//	localStorage.passwd = "123321";
//	localStorage.age = 18;
//	localStorage.setItem("sex", "小姐姐");
	//以上三种写法  修改数据一样适用! 其实系统就是看你操作的属性是否存在!属性不存在那就是新增,属性存储那就是修改!!
	//需要注意:localStorage只能存储字符串,如果存储的是数组或者其他类型数据;都会先转为字符串,再存储!!!!!!!!!
	console.log(localStorage);
	
	//3.查 就是获取值 从浏览器中取出值! 以下三种随便都可以!!只要属性名确实存在!就能取值!
	console.log(localStorage.username);
	console.log(localStorage["sex"]);
	console.log(localStorage.getItem("passwd"));
	//set赋值   get取值
	//item 中文翻译 条目;  属性名+属性值这样一对一对的数据,就是一个条目!!
	//4.删除  
//	localStorage.removeItem("sex");
//	localStorage.removeItem("phone");
	//5.清空操作
//	localStorage.clear();
	
	
	
</script>

```
![](https://img-blog.csdnimg.cn/3b3f6c3df3984c63abae013e2845de79.png)
![](https://img-blog.csdnimg.cn/7befdf609a4247bfa811acde6ecf1657.png)
