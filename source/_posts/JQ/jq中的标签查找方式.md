---
title: jq中的标签查找方式
date: 2020-12-26 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/1.jpg
banner_img: ../articleImages/1.jpg
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
		<ul>
			<li>列表1</li>
			<li>列表2</li>
			<li>列表3</li>
			<li>列表4</li>
			<li>列表5</li>
			<li>列表6</li>
		</ul>
		
		<input type="text" />
		<input type="password" />
		<input type="submit" disabled value="提交"/>
		<input type="checkbox" checked="checked"/>
		<!--disabled 不可用的-->
		<input type="text" disabled="disabled"/>
		<input type="radio" />
		<input type="button" value="普通按钮"/>
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>

<script type="text/javascript">
	
	//1. :first 找到jq对象中的第一个标签  常用!!!!!!!!!!!!!!
	$("li:first").css("background-color", "palegreen");
	//还可以这么写
	$("li").first().css("color", "#FF0000");
	//2. :last 找到jq对象中的最后一个标签  常用!!!!!!!!!!!!!!!!!!
	$("li:last").css("background-color", "yellow");
	//还可以
	$("li").last().css("font-size", "22px");
	//3. :even 找到jq对象中位置是偶数位置的标签
	$("li:even").css("border", "2px solid green");
	//4. :odd 找到jq对象中位置是奇数位置的标签
	$("li:odd").css("background-color", "pink");
	//5. :eq(index) 重点!特别常用!!!!!!!!!!!! 找到jq对象中位置是index的元素! index下标从0开始!!
	$("li:eq(3)").css("text-decoration", "line-through");
	//也可以
	$("li").eq(2).css("text-align", "center");
	//6. :gt(index) 找到jq对象中位置大于 index的元素,不包含index位置上的元素
	$("li:gt(3)").css("font-size", "30px");
	//7.  :lt(index) 找到jq对象中位置小于index的元素,不包含index位置上的元素
	$("li:lt(3)").css("background-color", "aquamarine");
	//8. 特别好用!! 特别常用!  siblings()除了本标签之外的其他所有的兄弟标签
	$("li").eq(2).siblings().css("display", "none");
	//9.查找父标签
	console.log($("li").parent());
	console.log($("li").parent().parent());
	
	//-------------------------------------
	//与表单相关的伪类选择器写法
	//1.找到所有的input标签
	console.log($("input"));
	//或者
	console.log($(":input"));
	//2.查找类型为text的input
	console.log($("input:text"));
	//3.查找类型为paddword的input
	console.log($("input:password"));
	//4.查找类型为radio的input
	console.log($("input:radio"));
	//等... 只要是 input中的type属性  都可以通过此方式查找
	//5.查找所有不可用的 input
	console.log($("input:disabled"));
	//6.查找所有可用的input
	console.log($("input:enabled"));
	//7.查找所有被选中的input 就是选中的单选框和复选框
	console.log($("input:checked"));
	
	
</script>
```
![](https://img-blog.csdnimg.cn/4997f192e7074f5d82e25986ab2f7564.png)
