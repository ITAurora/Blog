---
title: 前端HTML中的居中问题以及table表格的使用
date: 2020-03-02 10:10:10
tags:
  - HTML
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
		<style type="text/css">
			#one{
				/*让自身位置居中*/
				margin: 90px auto;
				/*让内部文本居中也包括行元素标签*/
				text-align: center;
				background-color: pink;
				width: 600px;
				height: 600px;
			}
			a{
				background-color: red;
			}
			span{
				background-color: blue;
			}
			h1{
				background-color: orange;
			}
			p{
				background-color: yellow;
			}
		</style>
	</head>
	<body>
		<div id="one">
			普通文本<br />
			<a href="###">百度</a><br />
			<span>这是一个span标签</span>
			<h1>这是一个h1</h1>
			<p>这是一个段落标签</p>
		</div>
	</body>
</html>

```
运行结果：
![](https://img-blog.csdnimg.cn/951a60a059bb46e19b7219430e2d21d4.png)

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<!--
			table 表格
			header 头部
			data 数据   date  日期
			th table-header 表头  行元素
			tr table-row row行 块元素
			td table-data 表中数据   行元素
			cell 单元格
			cellspaing 单元格之间的距离
			cellpadding 文字到边框的内填充距离
			colspan 横向合并
			rowspan 纵向合并
		-->
		<table border="1px" cellspacing="0px" 
			cellpadding="9px"
			width="30px"
			>
			<tr><th>Header</th>
				<th>0</th>
				<th>1</th>
				<th>2</th>
				<th>3</th>
				<th>4</th>
				<th>5</th>
			</tr>
			<tr><td>Data</td>
				<td colspan="3">0</td>
				<td rowspan="2">1</td>
				<td colspan="2" rowspan="2">2</td>
				<!--<td>3</td>-->
				<!--<td>4</td>
				<td>5</td>-->
			</tr>
			<tr><td>Data</td>
				<td>0</td>
				<td>1</td>
				<td>2</td>
				<!--<td>3</td>-->
				<!--<td>4</td>
				<td>5</td>-->
			</tr>
		</table>
	</body>
</html>

```
运行结果：
![](https://img-blog.csdnimg.cn/227d82d07426498f886d8febf12035c6.png)
