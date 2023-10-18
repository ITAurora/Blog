---
title: 利用jq写一个留言板
date: 2020-12-31 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/6.jpg
banner_img: ../articleImages/6.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>留言板</title>
		<link rel="stylesheet" type="text/css" href="css/01留言板.css"/>
	</head>
	<body>
		<!--留言板底部标签-->
		<div class="root">
			<!--输入框部分-->
			<ul class="content">
				<li>
					<input type="text" placeholder="输入标题" id="title"/></li>
				<li> 
					<textarea name="" rows="10"  cols="30" id="content" placeholder="请输入留言内容"></textarea>
				</li>
                 <li>
                 	<button id="btn">提交</button>
                 </li>                    
			</ul>
			<!---留言内容部分-->
			<div class="comment-list">
				<h2>显示留言</h2>
				<!--显示留言详细内容-->
				<ul>
					<!--准备 让1个li 来包括一条留言信息-->
					<!--<li class="box">
						<h3>张三</h3>
						<p>留言内容</p>
						<button class="delete-btn">删除按钮</button>
					</li>-->
					
				</ul>
			</div>
		</div>
		
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>

<script type="text/javascript">
	//提交留言的点击事件
	$("#btn").click(function(){
		var li = document.createElement("li");
		$(li).addClass("box");
		$(li).append("<h3>" + $("#title").val() + "</h3><p>" + $("#content").val() + "</p><button class='delete-btn'>删除</button>" );
		//每次最新的留言要放在最前面
		$(".comment-list ul").prepend($(li));
		//要在这里面写删除事件 因为是添加了留言之后才创建了删除按钮
		$(".delete-btn").click(function(){
			//this就是当前被点击的按钮
			$(this).parent().remove();
		})
		//清空输入框
		$("#title").val("");
		$("#content").val("");
		
	})
	
</script>

```
![](https://img-blog.csdnimg.cn/07b350dc18fe425a9d869b6088b049a2.png)
