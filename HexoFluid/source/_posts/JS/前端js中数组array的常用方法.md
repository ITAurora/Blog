---
title: 前端js中数组array的常用方法
date: 2020-11-09 12:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/4.jpg
banner_img: ../articleImages/4.jpg
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
	var hreo=["德莱文","托儿所","瑞文","妮蔻","石头人"]
	document.write(hreo+"<br />");
	//末位添加元素
	hreo.push("阿木木");
	document.write(hreo+"<br />");
	//删除最后一个
	hreo.pop();
	hreo.pop();
	document.write(hreo+"<br />");
	//在开头插入元素
	hreo.unshift('小学僧');
	document.write(hreo+"<br />");
	//删除开头元素
	hreo.shift();
	document.write(hreo+"<br />");
	//按照位置插入或者删除元素
	//下标为1的地方添加
	hreo.splice(1,0,"奥特曼");
	document.write(hreo+"<br />");
	//一次插入多个
	hreo.splice(2,0,"泰罗","迪迦");
	document.write(hreo+"<br />");
	//一边插入一边删除
	hreo.splice(1,2,"赛文","杰克","赛罗");
	document.write(hreo+"<br />");
</script>
```
运行结果：
![](https://img-blog.csdnimg.cn/12a7ca9c625f40d4aaa554371750eb4e.png)
