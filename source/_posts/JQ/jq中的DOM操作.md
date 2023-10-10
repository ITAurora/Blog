---
title: jq中的DOM操作
date: 2020-12-25 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/17.jpg
banner_img: ../articleImages/17.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>jq中的DOM操作</title>
	</head>
	<body>
		<div class="root"></div>
		<div id="box"></div>
		
		
		
		<button id="btn1">按钮1</button>
		<button id="btn2">按钮2</button>
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>
<script type="text/javascript">
	//1.创建标签还是js的写法!! jq中并没有封装此功能
	var p = document.createElement("p");
	
	
	// p变量是js版本的!!!!
	//js中 把 p 标签 放在指定的div中??
	/*
	var root = document.querySelector(".root");
	root.appendChild(p);
	*/
	//jq版本   把p标签放在div中!!
	//append()  在后面追加!!!    jq版本的添加子标签
	//$(".root").append(p); //可识别js版本变量
      $(".root").append($(p));//可识别jq版本的变量
      $(".root").append("<h1>这是大标题!</h1>");//可识别html字符串!
      //A.append(B)  将B放在A中!!!!
      //---------------------------
      var a = document.createElement("a");
      a.href = "http://www.baidu.com";
      //  B.appendTo(A)  将标签B放到标签A中!   to 是到达的意思!!
      $(a).appendTo($(".root"));
	//------------------------------------------------------------------------
	// A.prepend(B)   是将B标签放到A标签中最前面的位置
	$("body").prepend("<p>这是新增的p标签!!!</p>")
	// B.prependTo(A)  将B放到标签A中最前面的位置
	$("<span>普通的span标签</span>").prependTo($("body"));
	//append 和 prepend 都是父子关系!!
	//-------------------------------------------------------------------------
	
	// $(A).after(B) 在A元素的后面追加B元素; A和B是兄弟关系!!! 参数可识别html字符串,js变量,jq变量!!!  如果A元素选中了多个,那就是在每个A标签后面都追加!
	$("div").after("<h1>在div后面的大标题</h1>")
	
	//$(A).before(B) 在A元素的前面添加B元素. 同上!!!
	$("div").before("<em>这是倾斜标签</em>");
	
	//-------------------------------------------------------------
	
	//删除功能!!!!!
	/*
	 1. remove() 删除自己
	 2.detach() 删除自己
	 以上两个方法都有返回值, 返回的就是被删除的元素本身!
	 remove() 和 detach() 的区别
	 remove不但删除元素,也会移除元素绑定的事件!
	  detach方法只会删除元素,不会移除元素绑定的事件!!
	 */
	
	$("#btn1").click(function(){
		alert("按钮1被点击啦!!!");
	})
	
	$("#btn2").click(function(){
		alert("按钮2被点击啦!2222");
	})
	//看好啦!! 准备开始删除啦!!!  先删除  后添加!!
	var btn1 = $("#btn1").remove();
	$("body").append(btn1);
	
	var btn2 = $("#btn2").detach();
	$("body").append(btn2);
	
</script>

```
![](https://img-blog.csdnimg.cn/2ace28bef42b4002b63e43928ab4c664.png)
