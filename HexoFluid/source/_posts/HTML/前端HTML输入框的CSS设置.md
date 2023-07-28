---
title: 前端HTML输入框的CSS设置
date: 2020-03-07 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/1.jpg
banner_img: ../articleImages/1.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			#i1{
				width: 180px;
				height: 30px;
				padding-left: 10px;
				/*去掉默认带的外线框*/
				outline: none;
				/*重新设置边框*/
				border:1px solid lightgray;
				border-radius: 6px;
			}
			/*焦点选择器   只有标签获取焦点才会执行*/
			#i1:focus{
				border-color: skyblue;
			}	
		</style>
	</head>
	<body>
		
		<input type="text" id="i1" placeholder="请输入账号"/>
		<button>登录</button>
	</body>
</html>

```
运行结果：
![](https://img-blog.csdnimg.cn/431f977b09fd46b482b4ae9193fe2228.png)
![](https://img-blog.csdnimg.cn/db06e056fdf34226a7216cdc6d96a38f.png)

