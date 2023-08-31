---
title: js中的location对象
date: 2020-11-26 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/3.jpg
banner_img: ../articleImages/3.jpg
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
	//location对象中 最有用的方法
//以下将来都要放在事件中触发!!!
	//1.类似a标签的用法  就是通过js的方法  跳转网页
//	location.href = "http://www.jd.com";
	//2.重新加载本页面
//	location.reload();
   //3.替换本网页接口   功能跟第一个 href一致!!
//	location.replace("http://taobao.com"); 
	
	//以下 了解即可!!
	//1.获取窗口的url地址
	console.log(location);
	console.log(location.protocol);
	console.log(location.host);
	console.log(location.port);
	
	
	
</script>

```
运行结果:
![](https://img-blog.csdnimg.cn/e7567d3fe6f54ee482d4817a1a5af279.png)
