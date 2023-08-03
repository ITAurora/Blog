---
title: 前端HTMLrem单位的使用
date: 2020-03-14 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/17.jpg
banner_img: ../articleImages/17.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no" />
		<title></title>
		<style type="text/css">
			/*rem单位 参考html标签字号的大小
			  em单位 参考的是本标签字号的大小
			 */
			html{
				font-size: 10px;
			}
			div{
				width: 80%;
				margin: 30PX auto;
				border: 3px dashed red;
			}
			.div1{
				font-size: 4rem
			}
			.div2{
				font-size: 3rem
			}
			.div3{
				font-size: 2rem
			}		
			@media only screen and (max-width: 1000px) {
				html{
					font-size: 20px;
				}
			}
		</style>
	</head>
	<body>
		<div class="div1">
			这是第一段大文本这是第一段大文本这是第一段大文本这是第一段大文本
			这是第一段大文本这是第一段大文本这是第一段大文本这是第一段大文本
			这是第一段大文本这是第一段大文本这是第一段大文本这是第一段大文本
			这是第一段大文本这是第一段大文本这是第一段大文本这是第一段大文本
			这是第一段大文本这是第一段大文本这是第一段大文本这是第一段大文本
		</div>
		<div class="div2">
			这是的二段中等文本这是的二段中等文本这是的二段中等文本这是的二段中等文本
			这是的二段中等文本这是的二段中等文本这是的二段中等文本这是的二段中等文本
			这是的二段中等文本这是的二段中等文本这是的二段中等文本这是的二段中等文本
			这是的二段中等文本这是的二段中等文本这是的二段中等文本这是的二段中等文本
		</div>
		<div class="div3">
			这是第三段最小的文字这是第三段最小的文字这是第三段最小的文字这是第三段最小的文字
			这是第三段最小的文字这是第三段最小的文字这是第三段最小的文字这是第三段最小的文字
			这是第三段最小的文字这是第三段最小的文字这是第三段最小的文字这是第三段最小的文字
			这是第三段最小的文字这是第三段最小的文字这是第三段最小的文字这是第三段最小的文字
		</div>
	</body>
</html>

```
运行结果：
这是最大窗口
![](https://img-blog.csdnimg.cn/d4fae9c5cc8f424ca6e900f0079c1bab.png)
开始缩小窗口因为对窗口监听了 字号会同时变大
![](https://img-blog.csdnimg.cn/ff1d3407d2074fa483c834f94ceabff5.png)

