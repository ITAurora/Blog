---
title: 前端HTML伪元素的使用
date: 2020-10-18 12:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/2.jpg
banner_img: ../articleImages/2.jpg
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
			/*伪元素 通过css方式给标签的首或者尾添加一个标签*/
			.one:after{
				/*必写属性  默认是行元素属性*/
				content: "哈哈";
				/*正常标签css样式设置!!!*/
				background-color: salmon;
				color: yellow;
				font-size: 30px;
				width: 200px;
				display: block;
			}
			
			.one::before{
				content: "你好 世界!";
				
			}
			/*--------------*/
			.box{
				background-color: deeppink;
				position: relative;
			}
			
			/*使用伪元素   处理父子浮动塌陷问题!!!*/
			.box:after{
				content: "";
				clear: both;
				display: block;
				/*在父标签末尾追加一个 伪元素并且是块级特性
				 并且清除以上兄弟标签的影响 来撑起父元素高度!*/
			}
			
			
			
			.d1{
				width: 300px;
				height: 200px;
				background-color: palegreen;
				float: left;
			}
			.d2{
				width: 300px;
				height: 300px;
				background-color: palevioletred;
				float: left;
			}
			.over{
				width: 340px;
				height: 340px;
				background-color: rgba(0,0,0,0.4);
				position: absolute;
				left: 280px;
				top: -20px;
			}
		</style>
	</head>
	<body>
		<div class="one">
			<a href="###">京东</a>
			<p>段落块元素</p>
			<span>你呵呵</span>
		</div>
		
		
		
		
		<!--关键作用!!-->
		<div class="box">
			<div class="d1">1111111111</div>
			<div class="d2">2222222222</div>
			<div class="over">悬浮层</div>
			<!--::after clear:both;-->
		</div>
		
		<h1 style="background-color: salmon;">大标题</h1>
	</body>
</html>

```
运行结果：
![](https://img-blog.csdnimg.cn/0992c3fd120c44c3badf16e099d07a97.png)

