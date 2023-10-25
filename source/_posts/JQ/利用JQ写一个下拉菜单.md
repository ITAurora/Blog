---
title: 利用JQ写一个下拉菜单
date: 2021-1-5 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/11.jpg
banner_img: ../articleImages/11.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>下拉菜单</title>
		<style type="text/css">
			ul li{
				display: none;
			}
			
			
		</style>
	</head>
	<body>
		<div class="menu">
			<ul>
				<a href="###">衬衫</a>
				<li>测试1</li>
				<li>测试2</li>
				<li>测试3</li>
			</ul>
			<ul>
				<a href="###">西装</a>
				<li>测试1</li>
				<li>测试2</li>
				<li>测试3</li>
			</ul>
			<ul>
				<a href="##">小裙子</a>
				<li>测试1</li>
				<li>测试2</li>
				<li>测试3</li>
			</ul>
		</div>
		
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>
<script type="text/javascript">
	//ready()  jq版本的简写  等DOM标签加载完毕就会执行此函数,如果图片没有加载完成也会执行!!
	
	// $(function(){
		$(".menu a").click(function(){
			$(this).parent().find("li").slideDown().parent().siblings().find("li").slideUp();
			//等于
			// $(this).parent().find("li").slideDown()
			// $(this).parent().siblings().find("li").slideUp();
		})
		
		
		
	// })
	
	
	
</script>
```
![](https://img-blog.csdnimg.cn/eb078c579e86424a83306c4bfab8d0f5.png)
![](https://img-blog.csdnimg.cn/5ebe497ba6fd4849ba52a7d4df1d72ca.png)
