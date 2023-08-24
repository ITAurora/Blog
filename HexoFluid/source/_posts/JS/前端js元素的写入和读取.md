---
title: 前端js元素的写入和读取
date: 2020-11-19 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/6.jpg
banner_img: ../articleImages/6.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<div>
			哈哈哈 你说啥
			我听不见
			
			切~~~~~
			
			<p style="visibility: hidden;">这是一个段落标签</p>
			<!--注释 换种方式隐藏-->
			<h1 style="display: none;">这是一个大标题</h1>
		</div>
	</body>
</html>
<script type="text/javascript">
	/*
	 1.innerHTML innerText
	 以上适用于双标签,div,p,h1;既可以读取文本内容,也可以把文本写入到标签中
	 2.value 
	 适用于form表单 例如 input select等 既可以读取也可以写入
	 
	 
	 其他区别:
	 a.innerHTML 获取元素节点里的内容  包括文本结点 元素节点 注释节点并且保留空格
	 b.innerText 获取元素节点里的文本结点 忽略空格 不会显示隐藏元素的内容
	 ctextContent 获取元素节点中的文本结点 保留空格 会显示隐藏元素的的文本
	 
	*/
	var div=document.querySelector("div");
	console.log(div.innerHTML);
	console.log(div.innerText);
	console.log(div.textContent);
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/c6fecc7cceff49b389f19e625367787e.png)
