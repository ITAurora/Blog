---
title: 前端js中random随机数
date: 2020-11-09 10:10:10
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
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
	</body>
</html>
<script type="text/javascript">
	//随机数 js中默认产生0~1
	var a=Math.random();
	document.write(a+"<br />");
	//范围[0~20]
	//规则 [0~n] random()*n+1
	a=Math.floor(Math.random()*21);
	document.write(a+"<br />");
	//范围[20~90]
	//规则 [m~n] random()*(m-n+1)+m
	a=Math.floor(Math.random()*71+20);
	document.write(a+"<br />");
	document.write("练习1<br />");
	var b=0;
	for(var i=1;i<=10;i++){
		a=Math.floor(Math.random()*61+30);
		document.write(a+"<br />");
		b+=a;
	}
	document.write("和等于"+b+"<br />");
	document.write("练习2<br />");
	var a=0,b=0,c=70;
	for(var i=1;i<=10;i++){
		a=Math.floor(Math.random()*51+20);
		document.write(a+"<br />");
		var d=a>b?a:b;
		b=d;
		var e=a<c?a:c;
		c=e;
	}
	document.write("最大值"+d+"<br />");
	document.write("最小值"+e+"<br />");
	document.write("练习3<br />");
	var a=0,max=0,min=70;
	for(var i=1;i<=10;i++){
		temp=Math.floor(Math.random()*51+20);
		document.write(temp+"<br />");
		var max=temp>max?temp:max;
		var min=temp<min?temp:min;
	}
	document.write("最大值"+max+"<br />");
	document.write("最小值"+min+"<br />");
	
	
	document.write("练习3<br />");
	var max=0,min=80,max_index=0,min_index=0;
	for(var i=1;i<=10;i++){
		temp=Math.floor(Math.random()*71+10);
		document.write(temp+"<br />");
		if(max<temp){
			max=temp;
			max_index=i;
		}
		if(min>temp){
			min=temp;
			min_index=i;
		}
	}
	document.write("最大值"+max+"<br />");
	document.write("在第"+max_index+"位<br />");
	document.write("最小值"+min+"<br />");
	document.write("在第"+min_index+"位<br />");
</script>

```
运行结果：
![](https://img-blog.csdnimg.cn/16fc21602e184693ad0d2a9c60502f02.png)
