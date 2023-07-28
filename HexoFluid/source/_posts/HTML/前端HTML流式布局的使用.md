---
title: 前端HTML流式布局的使用
date: 2020-03-09 10:10:10
tags:
  - HTML
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
		<title>流式布局</title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			html, body{
				width: 100%;
				height: 100%;
			}
			.root{
				width: 70%;
				height: 50%;
				background-color: yellow;
				overflow: hidden;
				margin: 30px auto;
			}
			.one{
				width: 50%;
				height: 50%;
				/*margin-left: 25%;
				margin-top: 25%;*/
				background-color: skyblue;
			}
			
			ul{
				width: 90%;
				height: 600px;
				background-color: red;
				margin: 20px auto;
			}
			ul li{
				list-style: none;
				width: 32%;
				height: 200px;
				margin-right:2% ;
				margin-bottom: 2%;
				float: left;
			 background-color: yellowgreen;
			}
			ul li:nth-child(3n){
				margin-right: 0;
			}
			
		</style>
	</head>
	<body>
		<div class="root">
			<div class="one">
				
			</div>
			
		</div>
	<!------------------------------------->	
		<ul>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
		</ul>
	</body>
</html>

<!--
	流式布局也叫做百分比布局
	1.设置百分比,子标签宽高参考父标签宽高
	2.子标签的margin.padding 仅仅只参考父级的宽度!!
	3.既然是参考父标签  那么就要保证父标签有对应的确定的宽高!!
	
	
-->
```
运行结果：
![](https://img-blog.csdnimg.cn/d245df8789d14904a742df3dcd14314e.png)
![](https://img-blog.csdnimg.cn/8ac930269dd0462cabbeadaa35ce399b.png)


