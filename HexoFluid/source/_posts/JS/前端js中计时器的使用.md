---
title: 前端js中计时器的使用
date: 2020-11-11 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/7.jpg
banner_img: ../articleImages/7.jpg
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
	 计数器:
	 1.多次重复每个一段时间执行一次
	 setinterval(函数,时间);以毫秒为单位1000ms=1s
	 2.延时计时器 只会执行一次 是xxx毫秒后执行
	 setTimeOut(函数,时间);
	 3.清楚计时器
	  clearinerva(计时器编号);
	  注意:延时计时器只执行一次 无需清楚
	 */
	//形式1:
	var s1=setInterval(function(){
		document.write("你好!周一!!!<br />");
	},1000);
	//形式2:
	function hello(){
		document.write("你好!周二!!!<br />");
	}
	//只能写函数名 不能写()
	var s2=setInterval(hello,800)
	//形式3:
	var s3=setInterval("hello()",500)
	document.write(s1,s2,s3);
	//每个计时器的返回值就是自己的编号 从上往下执行
	//编号从1开始 清除计时器就是通过编号查找并清除
	//--------------------延时计时器----------------------
	//利用延时计时器(只会走一次 无需清除) 3s以后在清除
	setTimeout(function(){
		clearInterval(s1);
		clearInterval(s2);
		clearInterval(s3);
	},8000
	);
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/ac7642ec2c0d4a25a3331f4bdf4f1283.png)
一直弹出到结束:
![](https://img-blog.csdnimg.cn/79a0e7ddb6724a279e9b261263988ab3.png)

