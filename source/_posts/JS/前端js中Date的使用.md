---
title: 前端js中Date的使用
date: 2020-11-12 11:10:10
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
	//Date日期类
	//获取当前日期
	var date =new Date();
	//获取年
	var year=date.getFullYear();
	document.write(year+"<br />");
	//获取月
	//月份从0开始0~11
	var month=date.getMonth();
	document.write(month+1+"<br />");
	//获取日
	var dat=date.getDate();
	document.write(dat+"<br />");
	//获取星期几
	var day=date.getDay();
	document.write(day+"<br />");
	//获取小时
	var hours=date.getHours();
	document.write(hours+"<br />");
	//获取分钟
	var minute=date.getMinutes();
	document.write(minute+"<br />");
	//获取秒
	var seconds=date.getSeconds();
	document.write(seconds+"<br />");
	//获取毫秒
	var milliseconds=date.getMilliseconds();
	document.write(milliseconds+"<br />");
	//获取时间戳 就是用来计算日期差
	//时间戳:就是1970年1月1日00;00;00到某个日期的毫秒
	var time=date.getTime();
	document.write(time+"<br />");
	//nwe Date(); 获取此时此刻系统的时间
	//我们可以自己赋值 年 月(月是从开始) 日
	var d1 = new Date("2022", "2", "14");
	document.write(d1);
	var d2 = new Date("2021", "7", "19", "23", "19", "10");
	document.write(d2);
	var d3 = new Date(1289378978973);//时间戳
	document.write(d3);
	document.write(d3.getFullYear() + "年" + (d3.getMonth() + 1)  + "月" + d3.getDate() + "日 " + d3.getHours() + ":" + d3.getMinutes() + ":" + d3.getSeconds());
	
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/590737f99e8e4cdcabf99bf77bfb275e.png)
