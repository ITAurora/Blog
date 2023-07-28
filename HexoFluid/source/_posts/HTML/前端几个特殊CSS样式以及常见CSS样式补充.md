---
title: 前端几个特殊CSS样式以及常见CSS样式补充
date: 2020-02-26 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/5.jpg
banner_img: ../articleImages/5.jpg
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
				background-color: pink;
				color: red;
			}
			/*a标签的字体颜色，必须直接修改a标签的属性*/
			#one a{
				/*去下划线*/
				text-decoration: none;
				
			}
			#two{
				background-color: black;
			}
			/*默认内容撑起高度，但在底部会有间隙*/
			/*如果不对img进行设置背景底部会多出一点边框*/
			#two img{
				/*vertical 竖直方向*/
				vertical-align: bottom;
			}
		</style>
	</head>
	<body>
		<div id="one">
			<span>这是span，用来对比</span><br />
			<a href="###">哈哈哈哈</a><br />
			<a href="">哈哈哈哈</a><br />
			<a>这是一个不带网站的a标签</a>
		</div>
		<div id="two">
			<img src="img/1.jpg"/>
		</div>
	</body>
</html>

```
运行结果：
![](https://img-blog.csdnimg.cn/a2d72b7fad7844569bd8895f6d72ff73.png)

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			#one{
				/*1.背景色单词写法*/
				background-color: salmon;
				/*0~255 红 绿 蓝*/
				background-color: rgb(255, 255, 100);
				/*2.字母间距，默认normal正常
				 相当于0px 可以设置负值*/
				letter-spacing: 5px;
				/*3.单词间距
				 默认normal正常 相当于0px 可以设置负值
				 */
				word-spacing: 5px;
				/*4.文字修饰线
				 underline 下划线
				 overline 上划线
				 line-through 删除线
				 none 没有线
				 */
				text-decoration: line-through;
				/*5.首行缩进
				 一，数值 px
				 二，em单位 em是参考当前标签font-size字号值
				 例如当前字号为16px那么1em=16px 2em=32px
				 如果当前字号20px 1em=20px
				 */
				text-indent: 2em;
				/*6.行高*/
				line-height: 50px;
				/*7.标签宽度*/
				width: 260px;
				height: 100px;
				/*8.文本溢出处理方式
				 clip: 裁剪掉
				 ellipsis：用省略号代替*/
				/*text-overflow: ellipsis;需要搭配其他设置*/
				/*文本溢出换成省略号效果单行省略多行省略百度找*/
				white-space: nowrap;
				/*nowrap意思是不让换行*/
				text-overflow: ellipsis;
				/*overflow: hidden;超出部分隐藏*/
				overflow: hidden;
				/*9.大小写转换 作用于英文
				 capitalize首字母大写
				 uppercase 全部大写
				 lowercase 全部小写*/
				text-transform: uppercase;
				
				
			}
			#two{
				/*a透明度0~1取值 仅仅是背景色透明化*/
				background-color: rgba(255, 255, 100, 0.3);
				width: 100px;
				height: 40px;
				/*两行省略*/
				text-overflow: -o-ellipsis-lastline;
                overflow: hidden;
                text-overflow: ellipsis;
                display: -webkit-box;
                -webkit-line-clamp: 2;
                -webkit-box-orient: vertical
			    }
		</style>
	</head>
	<body>
		<div id="one">
			<!--英文只认空格-->
			hello hi 123456789 
		</div>
		<div id="two">
			萨芬看来你看是否能恐怕都是亏损
		</div>
	</body>
</html>

```
运行结果：
![](https://img-blog.csdnimg.cn/c9a88449ef1547b09cbf2ebd61f3bfbd.png)
