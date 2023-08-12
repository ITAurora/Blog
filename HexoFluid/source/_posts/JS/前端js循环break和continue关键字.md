---
title: 前端js循环break和continue关键字
date: 2020-11-06 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/16.jpg
banner_img: ../articleImages/16.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```js
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
	</head>
	<body>
		
		<!--
			break 结束一层循环
			continue 跳过本次循环
		-->
	</body>
</html>
<script type="text/javascript">
	document.write("<h1>break</h1>");
	for(var i = 1; i <= 50; i++){
		if(i == 20){
			document.write("有虫子"+"<br />");
			break;
		}
		document.write(i+"<br />");
	}
	document.write("<h1>continue</h1>");
	for(var i = 1; i <= 50; i++){
		if(i == 20){
			document.write("有虫子"+"<br />");
			continue;
		}
		document.write(i+" ");
	}
</script>
```
运行结果：
![](https://img-blog.csdnimg.cn/2ecd536d0b1142648af730c1b1604380.png)
