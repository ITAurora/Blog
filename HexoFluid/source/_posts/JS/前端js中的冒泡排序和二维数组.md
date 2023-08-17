---
title: 前端js中的冒泡排序和二维数组
date: 2020-11-12 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/9.jpg
banner_img: ../articleImages/9.jpg
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
	var arr=[29,80,16,38,6,12];
	//外层循环负责比较几轮
	for(var i=0;i<arr.length-1;i++){
		//内层循环负责每轮比较的次数
		//大于小于决定顺序逆序排序
		for(var j=0;j<arr.length-1-i;j++){
			if (arr[j]>arr[j+1]) {
				var temp=arr[j];
				arr[j]=arr[j+1];
				arr[j+1]=temp;
			}
		}
	}
	document.write(arr);
</script>
```
运行结果:![](https://img-blog.csdnimg.cn/5a0b456d8bda4d6281403d53b8756af5.png)

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			
		</style>
	</head>
	<body>
		
		
	</body>
</html>
<script type="text/javascript">
	//二维数组 本质上就是多个一位数组
	var arr=[
	[15,465,879,312,645,132,],
	["呵呵","哈哈","123"],
	[1.1,3.1415926,456],
	[true,false,undefined,18]
	];
	document.write(arr+" "+"<br />");
	console.log(typeof arr);
	document.write(arr[0][3]+" "+"<br />");
	//二维数组 双下标[行][列]
	for (var i=0;i<4;i++) {
		for (var j=0;j<4;j++){
			document.write(arr[i][j]+" ");
		}
		document.write("<br />");
	}
	for (var i=0;i<arr.length;i++) {
		for (var j=0;j<arr[i].length;j++){
			document.write(arr[i][j]+" ");
		}
		document.write("<br />");
	}
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/a389ccdebd154f6b86f18d865cbf088e.png)

