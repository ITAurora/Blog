---
title: 前端js中while循环
date: 2020-11-06 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/1.jpg
banner_img: ../articleImages/1.jpg
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
	//while循环
//	while(条件真假){
//		条件为真 执行
//		为假 不执行
//	}
//10亿每天花一半
var i=0;
while(i<=10){
	document.write(i+"<br />");
	i++;
}
var i=1000000000,a=0;
while(i>1){
	i/=2;
	document.write(Math.floor(i)+"<br />");
	a++;
}
document.write(a+"天<br />");
do{
	document.write("do先执行<br />");
}while(false){
	document.write("while执行<br />");
}
</script>

```
运行结果：
![](https://img-blog.csdnimg.cn/5f5b546765cf439d9140d749dda2023e.png)

