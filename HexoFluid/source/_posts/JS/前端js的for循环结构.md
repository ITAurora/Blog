---
title: 前端js的for循环结构
date: 2020-03-23 13:10:10
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
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		
	</body>
</html>
<script type="text/javascript">
	/*for 循环
	 * for(循环变量初始化1 循环条件2 循环自变4){
	 * 	循环体3
	 * }
	 * 执行顺序为
	 * 1 2 3 4 2 3 4 2 3.......
	 */
	for(var i=1;i<=10;i++){
		document.write("哈哈<br />")
	}
	document.write("<br />")
	for(var i=1;i<=100;i++){
		document.write(i+" ")
	}
	//--------------------
	document.write("<br />")
	//练习:1~100之间的偶数
	for(var i=1;i<=100;i++){
		if (i%2==0) {
			document.write(i+" ")
		}
	}
	document.write("<br />")
	//7的倍数
	for(var i=1;i<=100;i++){
		if (i%7==0) {
			document.write(i+" ")
		}
	}
	document.write("<br />")
	//个位数为7的
	for(var i=1;i<=100;i++){
		if (i%10==7) {
			document.write(i+" ")
		}
	}
	document.write("<br />")
	//十位数为7
	for(var i=1;i<=100;i++){
		if (i/10>7&&i/10<8) {
			document.write(i+" ")
		}
	}
	document.write("<br />")
	for(var i=1;i<=100;i++){
		if (!(i%7==0||i%10==7||Math.floor(i/10)==7)) {
			document.write(i+" ")
		}
	}
	document.write("<br />")
	
	//---------------------
	for(var i=1;i<=6;i++){
		for(var a=1;a<=6;a++){
			document.write(a+" ")
	    }
		document.write("<br />")
	}
	for(var i=1;i<=6;i++){
		for(var a=1;a<=i;a++){
			document.write(a+" ")
	    }
		document.write("<br />")
	}
	for(var i=6;i>=1;i--){
		for(var a=1;a<=i;a++){
			document.write(a+" ")
	    }
		document.write("<br />")
	}
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/0e0e22b59716492d93cdf14a3221cbc6.png)
