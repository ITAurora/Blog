---
title: 前端HTML网页文档模板介绍以及常用标签
date: 2020-02-22 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
cover: ../articleImages/1.jpg
feature: true
---
<meta name="referrer" content="no-referrer"/>

```html
<!--此为注释，注释不执行-->
<!--DOCTYPE document type 指定当前文档类型为html-->
<!DOCTYPE html>
<!--编码正式开始的区域，html是最大的标签-->
<html>
	<!--head 网页的头部相当于手机中的设置功能，主要负责网页的设置信息-->
	<head>
		<!--mete 设置一些网页格式，charset字符集，utf-8万国码 为了识别中文不会乱码-->
		<meta charset="UTF-8">
		<!--title 设置网页的标题-->
		<title>这是一个网页标题</title>
	</head>
	<!--body 网站内容的展示区域文字和图片放这里面-->
	<body>
		这是网页的内容
	</body>
</html>
```
运行结果：![在这里插入图片描述](https://img-blog.csdnimg.cn/a7ea8b6f9c384816995021d2cd5c2297.png)

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>这是一个网页标题</title>
	</head>
	<body>
		<!--补全代码enter键或者Tap键->
		<!--1.标题标签 h1~h6字号加粗，并且字号逐级减小
			字号逐级减小.标题标签自动加粗
             h1 == 32px
             h2 == 24px
             h3 == 18.72px
             h4 == 16px
             h5 == 13.28px
             h6 == 12px
                 当前主流的浏览器可识别的文本大小极限最小的是12px.
                 默认字号都是16px.-->
		<h1 style="background: red; width: 100xp;height: 100xp;">一一一</h1>
		<h2 style="background: orange;">二二二</h2>
		<h3 style="background: yellow;">三三三</h3>
		<h4 style="background: green;">四四四</h4>
		<h5 style="background: blue;">五五五</h5>
		<h6 style="background: orchid;">六六六</h6>
		<!--2.段落标签 p
			文本从上自下，从左往右顺序排版，不识别手动换行
			需要设置换行标签<br />
			默认字号为16xp，为正常不加粗字体
		-->
		<!--转义字符&nbsp;表示空格-->
		<p>
			遇事不决，可问春风。<br />
			春风不语，可随本心。
		</p>
		<!--3.倾斜标签 em-->
		<em style="background: olive;">这是一个倾斜斜标签&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</em><br />
		<!--4.加粗标签 strong-->
		<strong>这是一个加粗标签</strong><br />
		<!--5.图片标签 img
			src属性：给图片设置路径
			可以是本地资源，也可以是网络图片链接
			alt属性：图片路径报错提示
		-->
		<img src="img/100.jpg"alt="图片路径出错"/><br />
		<img src="https://tse3-mm.cn.bing.net/th/id/OIP-C.AQI3RuWHZcbjp0rdTbAeLgHaHa?pid=ImgDet&rs=1"/><br />
		<img width="475xp" height="500xp" src="img/1.jpg"/>
		<!--6.a超链接标签
			href属性：网址地址
			href="" 刷新网页并返回顶部
			#占位符
			href="#" 不刷新网页但会返回顶部
			href="###" 不刷新也不会返回顶部 
		-->
		<a href="http://baidu.com">百度</a>
		<a href="">京东</a><br />
		<a href="#">淘宝</a><br />
		<a href="###">支付宝</a><br />
		<!--7.无意义的标签 块元素 div
			但很重要，很常用，一般用来设置网页布局
		-->
		<div id="">
			无意义的块元素，块元素独占一行，默认宽度参考父级宽度，高度由内容撑起，也能手动控制宽高
		</div>
		<div class="">
			无意义的块元素，默认宽度参考父级宽度，高度由内容撑起，也能手动控制宽高
		</div>
		<!--8.无意义的行元素 span-->
		<span id="">
			无意义的行元素，行元素相邻会共行展示
		</span>
		<span id="">
			无意义的行元素，行元素相邻会共行展示
		</span>
</html>
```
运行结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/a8ccfaecb66e4b5eb3b7cd4150a62a2a.png)

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<!--1.列表标签
			ol 有序列表
			ul 无序列表
			dl 自定义列表
		-->
		<ol>
			<li>1111111</li>
			<li>2222222</li>
			<li>3333333</li>
		</ol>
		
		<ul>
			<li>1111111</li>
			<li>2222222</li>
			<li>3333333</li>
		</ul>
		<!--自定义
			t title 标题
			d data 数据正文
		-->
		<dl>
			<dt>服装</dt>
			<dd>男装</dd>
			<dd>女装</dd>
			
			<dt>食品</dt>
			<dd>薯片</dd>
			<dd>巧克力</dd>
		</dl>
	</body>
</html>

```
运行结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/86708c4275f9477194be7618f9e4a080.png)


