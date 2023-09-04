---
title: 前端js中的switch
date: 2020-11-05 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/14.jpg
banner_img: ../articleImages/14.jpg
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
	var phone=606;
	switch (phone){
		case 601:
		console.log("市场部1")
			break;
		case 602:
		console.log("市场部2")
			break;
		case 603:
		console.log("市场部3")
			break;
		case 604:
		console.log("市场部4")
			break;
		case 605:
		console.log("市场部5")
			break;
		case 606:
		console.log("市场部6")
			break;
		default:
		console.log("打错了")
			break;
	}
	var month=2;
	switch (month){
		case 1:
		case 3:
		case 5:
		case 7:
		case 8:
		case 10:
		case 12:
		console.log("31天")
			break;
		case 2:
		console.log("28天||29天")
			break;
		case 4:
		case 6:
		case 9:
		case 11:
		console.log("30天")
			break;
		default:
		console.log("您输错啦")
			break;
	}
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/74d54287b7c54ca2bdc51b4eada34267.png)
