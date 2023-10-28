---
title: json解析
date: 2021-1-8 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/14.jpg
banner_img: ../articleImages/14.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>json解析</title>
		<link rel="stylesheet" type="text/css" href="layui/css/layui.css"/>
	</head>
	<body>
		<table class="layui-table" style="width: 500px !important;">
		<tr>
			<th>编号</th>
			<th>姓名</th>
			<th>年龄</th>
			<th>性别</th>
			<th>操作</th>
		</tr>
		</table>
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>

<script type="text/javascript">
	/*
http https(加密) 超文本传输协议!
数据格式: json格式
类似.jpg .png .word .txt  .js .css .html等

 json的优势:
 其数据格式就是容器的混搭. [] {}这两种容器的相互嵌套!!
*/
	//声明一个json格式的字符串
	var jsonStr = '[{"id":1,"name":"张三","age":20,"sex":"男"}, {"id":2, "name":"李四","age":28,"sex":"男"}, {"id":3,"name":"王五","age":23,"sex":"男"}, {"id":4,"name":"赵六","age":30,"sex":"男"}]';
	console.log(jsonStr);
	
	/*
	 json字符串解析,其实本质上就是把json字符串转化成我们js中学习过的一些数据结构,比如数组[] 对象键值对{}等 
	 解析格式:
	 JSON.parse(json格式字符串) 其返回值就是[] 或者是{} 需要看json字符串最外层的容器是[]的话,解析完就是数组! 最外层符号是{},解析完就是对象;
	*/
	var arr = JSON.parse(jsonStr);
	console.log(arr);
	//------------
	//最外层的容器是{}的json字符串!!
	var str2 = '{"status":200, "totalCount":100, "message":"请求成功!", "data":[{"id":1,"name":"张三","age":20,"sex":"男"}, {"id":2, "name":"李四","age":28,"sex":"男"}, {"id":3,"name":"王五","age":23,"sex":"男"}, {"id":4,"name":"赵六","age":30,"sex":"男"}]}';
	var obj = JSON.parse(str2);
	console.log(obj);
	
	console.log(obj.status);
	console.log(obj.totalCount);
	console.log(obj.message);
	
	var dataArray = obj.data;
	for(var i in dataArray){
		var tr = document.createElement("tr")
		$("table").append(tr);
		
//		取出对象
        var s = dataArray[i];
		//数据写入td中
		var td1 = document.createElement("td");
	    $(td1).html(s.id);
	    $(tr).append(td1);
	    
	    var td2 = document.createElement("td");
	    $(td2).html(s.name);
	    $(tr).append(td2);
	    
	    var td3 = document.createElement("td");
	    $(td3).html(s.age);
	    $(tr).append(td3);
	    
		var td4 = document.createElement("td");
	    $(td4).html(s.sex);
	    $(tr).append(td4);
	    
	    var td5 = document.createElement("td");
	    $(td5).html("<button class='layui-btn layui-btn-warm layui-btn-sm'>编辑</button><button class='layui-btn layui-btn-normal layui-btn-sm'>删除</button>");
	    $(tr).append(td5);
	    
		
	}
	//----------------------------------------------
	//对象如何转回json字符串呢???
	var s1 = JSON.stringify(arr);
	console.log(s1);
	var s2 = JSON.stringify(obj);
	console.log(s2);
</script>


```
![](https://img-blog.csdnimg.cn/8ebeb9d47def484db4ae965e776b8207.png)
