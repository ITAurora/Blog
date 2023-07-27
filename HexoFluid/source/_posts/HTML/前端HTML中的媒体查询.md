---
title: 前端HTML中的媒体查询
date: 2020-03-10 10:11:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/6.png
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
			.one{
				width: 300px;
				height: 300px;
				background-color: pink;
			}
			/*监听的是浏览器窗口的大小     最小能监听到的范围*/
			@media only screen and (min-width: 800px) {
				body{
					background-color: yellow;
				}
			}
			/*最大能监听到的宽度是600px*/
			@media only screen and (max-width: 600px) {
				#one{
					background-color: seagreen;
				}
			}
			/*@media only screen and (min-width: 500px) and (max-width: 1000px) {
				body{
					background-color: yellow;
				}
			}*/
		</style>
	</head>
	<body>
		<div class="one">
			
		</div>
	</body>
</html>
<!--
	媒介查询
	其实是监听对象的宽度或者高度 并且设置一个临界值 当达到临界值时 触发媒介查询里对应的代码 
对页面进行修改
	语法：
	@media 监听设置类型 and (设置临界值){
		设置需要修改的布局的代码
	}
	监听设备类型：
	1.only screem (默认且重点而且常用) 用于手机 平板 电脑
	2.print 打印机
	3.speech 读音设备
	4.all 所有设备
-->

```
运行结果：
![](https://img-blog.csdnimg.cn/2685856fb21746c19599559b84c6cdff.png)
当窗口缩小时
![](https://img-blog.csdnimg.cn/e43c339f6df54582a5f2746843236384.png)
会根据你窗口大小发生变化