---
title: 前端CSS的引用方式以及的CSS样式
date: 2020-10-11 11:10:10
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
		<title></title>
		<style type="text/css">
			/*css编码区域*/
			div{
				background-color: royalblue;
				height: 300px;
				width: 300px;
			}
			p{
				background-color: yellow;
				height: 100px;
				width: 300px;
			}
		</style>
		<!--3.引用外部css文件 再head中设置-->
		<link rel="stylesheet" type="text/css" href="css/index.css"/>
		
	</head>
	<body>
		<!--注意 范围越小 优先级越高--->
		<!--1.行间引入css 不常用-->
		<div style="width: 200px;height: 100px;background-color: red;">这是行间引用css</div>
		<div>这是第一个内部引用css的div</div>
		<p>这是一个内部引用css的p标签</p>
		<div>这是第二个内部引用css的div</div>
		<h1>这是一个外部引用css的h1标题</h1>
	</body>
</html>

```

运行结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/f0933f1ed1ea41eba18f8d20c261b0ba.png)

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			div{
				/*背景颜色*/
				background-color: hotpink;
				/*北京宽度*/
				width: 1000px;
				/*背景高度*/
				height: 200px;
				/*字号*/
				font-size: 66px;字体颜色
				/**/
				color: royalblue;
				/*字体风格*/
				font-family: "franklin gothic book";
				/*字体加粗
				 100~500 正常
				 600~900 加粗
				 bold或者bolder
				 */
				font-weight: 600;
				/*文本对其方式 默认靠左*/
				text-align: center;
				/*行高
				 注意：技巧 height标签高==line-height行高
				 只适用于 单行文本上下剧中
				 */
				line-height: 200px;
			}
		</style>
	</head>
	<body>
		<div>天不生我李淳罡，剑道万古如长夜<br/>
			一二三四五，上山打老虎
		</div>
	</body>
</html>

```
运行结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/871d58f8e6d047c8ade7744e37c09c7c.png)
