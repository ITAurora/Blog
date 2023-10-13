---
title: jq中的this属性
date: 2020-12-28 10:10:10
tags:
  - JQ
categories:
  - JQ
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
		<title>jq中的this</title>
	</head>
	<body>
		<ul>
			<li>列表1</li>
			<li>列表2</li>
			<li>列表3</li>
			<li>列表4</li>
			<li>列表5</li>
			<li>列表6</li>
			<li>列表7</li>
			<li>列表8</li>
			<li>列表9</li>
			<li>列表10</li>
		</ul>
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>
<script type="text/javascript">
	
	$("li").click(function(){
		//js版本的this  没什么特别的!
		console.log(this);
		//jq版本的this  
		console.log($(this));
		//但是jq版本的this 自带index()方法!  index中存储的就是 点击的标签在jq对象中的下标!
		//console.log("js中的this", this.index());//报错 js中的this 没有index
		//下标从0开始!!
		console.log("jq中的this", $(this).index());//特别好用!!不需要你来设置!!!
	})
	
	
	
</script>

```
![](https://img-blog.csdnimg.cn/7432668441ca42919c3633f7daba9069.png)
