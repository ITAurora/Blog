---
title: 前端利用js修改标签内容
date: 2020-03-22 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/11.jpg
banner_img: ../articleImages/11.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```js
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		
		<div class="one">111</div>
		<p>pppp</p>
		<input type="text" value="默认值"/>
		<a href="###" id="a1">超链接</a>
		<div id="box">
			<span>span行元素</span>
		</div>
		
	</body>
</html>
<script type="text/javascript">
	
	var one = document.getElementsByClassName("one")[0];
	one.style.backgroundColor = "pink";
	one.style.height = "100px";
	
	//1.写入文档  
	/*
	 缺点:
	 1.不能写入指定的标签中!
	 2.直接写入body中
	 优点: 不会新数据覆盖旧数据!每次写入的数据都会自动拼接!! 
	 */
	document.write("哈哈哈你好!!");
	document.write("0000789789!!");
	document.write("<h1>大标题</h1>");
	//2. innerHTML 重点!! 即可给标签赋值  也可 对标签取值!!
	/*
         优点:
     1.既能写入文本字符串,也能直接写标签
     2.可以指定写入某个父标签中,不会直接写入body
         缺点:新数据会覆盖旧数据!   但是可以通过  += 来解决!!
     */
          one.innerHTML = "周润发";
          console.log(one.innerHTML);
           one.innerHTML = one.innerHTML + "周星驰";
	     one.innerHTML += "<p>直接写入标签</p>";
	     
	     
	     //3. innerText  既可给标签赋值  也可 对标签取值!!
	     /*
	    特点: 只能写入字符串,不识别标签字符串.也是新数据覆盖旧数据!
	      */
	     var p = document.getElementsByTagName("p")[1];
	     p.innerText = "哈哈";
	     p.innerText += "<a href='###'>京东</a>"
	     
	     //4.注意注意!重点!  给input赋值或者取值  只能通过value
	     var i1 = document.getElementsByTagName("input")[0];
	     i1.value = "哈哈哈哈我试试!";
	     i1.value += "肯定可以拼接!";
	     console.log(i1.value);
</script>

```
运行结果:
![](https://img-blog.csdnimg.cn/9b6ed26bc931426c9829053a944139c3.png)

