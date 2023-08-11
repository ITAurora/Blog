---
title: 前端js语法基础
date: 2020-11-02 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/6.jpg
banner_img: ../articleImages/6.jpg
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
		<!--行间引入js  不推荐  知道即可-->
		<a href="javascript:alert('今天是星期一!')">点击弹出提示框</a>
		
	</body>
</html>

<!--内部引入 -->
<script type="text/javascript">
			//在此处编译js代码即可!!
			//变量  标识符var
			var a = "哈哈";
			//console控制台  log输出
			console.log(a);
			//弹框
			alert("你看这是弹框!");
			
</script>

<!--外部引入-->
<script src="js/main.js" type="text/javascript" charset="utf-8">
	//注意!此处虽然是双标签,但是不可以写任何代码!写了也不会执行!
	//不信你看!
	console.log("我非要写,我就想看看这行输出走不走!!");
		
		
</script>

```
运行结果:
![](https://img-blog.csdnimg.cn/e8375e25242647698045b9a22d50b7f5.png)
![](https://img-blog.csdnimg.cn/54ecd3b5db1c4a88a67caa8d78fe4628.png)
![](https://img-blog.csdnimg.cn/7568760d49534cefb02c8d8c2d1488a5.png)

