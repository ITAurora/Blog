---
title: 前端js创建标签和插入标签
date: 2020-11-20 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/10.jpg
banner_img: ../articleImages/10.jpg
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
		<div class="box"></div>
		<div class="root"></div>
	</body>
</html>
<script type="text/javascript">
	//1.获取标签
	var box=document.querySelector(".box");
	var rot=document.querySelector('.root');
	//2.创建一个元素节点 --------非常重要
	var img=document.createElement('img');
	console.log(img,typeof img);
	//3.将标签插入-------------非常重要
	box.appendChild(img);
	//4.设置属性
	img.src="img/1.jpg";
	//5.通过innerHTML新增一个子标签
//	box.innerHTML+="<h1 class='tittle'>大标题</h1><p class='info'>段落标签</p>";
	//推荐:创建大模块使用create+append 里面的小模块用innerHTML
	
	//6.再创建一个a标签 放入box
	var a=document.createElement("a");
	a.href="http://www.baidu.com";
	a.innerHTML="百度一下";
	box.appendChild(a);//拼接在父标签中最后的位置
	//7.再创建一个h2标签 要求放在box第一个子标签位置
	var h2=document.createElement("h2");
	h2.innerHTML="哈哈哈哈哈哈";
	h2.style.backgroundColor="red";
	//innerBefore(新元素,指定元素); 将新元素插在指定元素前面
	box.insertBefore(h2,box.firstElementChild);
	//8.删除指定的子标签
//	document.body.removeChild(rot);
	//9.删除在自己个!!!!注意!深处本标签,会连带着自身中的子标签都删掉
//	box.remove();
	//10.替换标签  replace(新标签,旧标签);
	var h3=document.createElement("h3");
	h3.innerHTML="周五了周五了";
	//h3替换h2
	box.replaceChild(h3,h2);
	//11.删除box中的img
	box.removeChild(img);

</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/a0e8b460cf434bf09eaa688c84202b2d.png)
