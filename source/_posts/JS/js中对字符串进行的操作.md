---
title: js中对字符串进行的操作
date: 2020-12-11 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/4.jpg
banner_img: ../articleImages/4.jpg
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
	</body>
</html>
<script type="text/javascript">
	
	var str1 = "abc哈哈呵呵123你好";
	//1.获取子字符串 截图字符串
	//substr(从哪个下标开始, 长度);
	var s1 = str1.substr(3, 4);
	console.log(s1);
	//2.获取某个字符的下标  不存在就返回-1
	var index = str1.indexOf("呵");//数组中也有这个方法  用法一样
	console.log(index);
	//3.替换字符串
	var s2 = str1.replace("哈哈", " hello");
	console.log(s2);
	//4.去掉首尾 空格  只能去除首尾
	var str2 = " a b c ";
	var s3 = str2.trim();
	console.log(str2);
	console.log(s3);
	//5.将一个字符串 按照某个符号 分隔成数组
	var str3 = "哈,呵呵,你好,哎呀,吃饭啦";
	var arr = str3.split(",");//以, 为分隔符号
	console.log(arr);
	str3 = "哈 呵呵 ac sn";
	console.log(str3.split(" "));//以空格分隔
	str3 = "你好,呵呵 哈哈 abc,bvc";//既有空格 也有逗号
	console.log(str3.split(/ |,/)); //这是正则表达式的写法  明天会详细讲今天可以试试
	str3 = "abcdfhg,哈哈 呵呵";
	console.log(str3.split(""));//不写分隔符  那就是每个字符都单独分隔
	
</script>
```
![](https://img-blog.csdnimg.cn/3bb5a60e070d4bc1a6eb34c9bd1cdf21.png)
