---
title: 利用js写一个简单的留言板
date: 2020-11-21 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/11.jpg
banner_img: ../articleImages/11.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

css样式:

```css
*{
	margin: 0;
	padding: 0;
}
ul{
	list-style: none;
}

.root{
	width: 500px;
	/*增加新的留言  父级高度也会变大!  高度不要设置*/
	padding: 20px;
	border: 3px solid red;
	margin: 30px auto;
	

}

#title, #content{
	width: 480px;
	outline: none;
	border-radius: 5px;
	border: 1px solid lightgray;
	padding: 0 10px;
}
.content li{
	margin-bottom: 20px;
}
#title{
	height: 30px;
}
#title:focus, #content:focus{
	border-color:skyblue;
}
#content{
	font-size: 18px;
	padding: 10px;
}
#btn{
	width: 80px;
	height: 30px;
	float: right;
}
/*-------------*/
.comment-list{
	margin-top: 70px;
}

.box{
	/*background-color: seagreen;*/
	overflow: hidden;
}
.box h3{
	background-color: sandybrown;
	display: inline-block;
	padding: 10px;
}
.box p{
	background-color: yellowgreen;
	margin: 10px 0;
	padding: 10px;
}
.box .delete-btn{
	float: right;
	width: 100px;
	height: 35px;
}

```
js代码:

```js
//1.获取标签
var titleEl = document.querySelector("#title");
var contentEl = document.querySelector("#content");
var addBtn = document.querySelector("#btn");
var ul = document.querySelector(".comment-list ul");
//2.


//3.事件函数
//提交留言
addBtn.onclick = function(){
	//1.获取输入框中的值
	var title = titleEl.value;
	var content = contentEl.value;
	//2.简单判断  不能为空
	if(title == "" || content == ""){
		alert("请正确输入内容!");
		return;//直接结束代码!!
	}
	//清除输入框中的内容
	titleEl.value = "";
	contentEl.value = "";
	
	//3.标题和内容不为空
	//创建li标签 class为box
	var li = document.createElement("li");
	li.className = "box";
	//--------注意这里!!!!
	//每次留言要放在最前面
	if(ul.childElementCount == 0){
		//此时 还没有任何留言
		ul.appendChild(li);
	}else{
		//不为0 说明已经存在留言信息了
		ul.insertBefore(li, ul.firstElementChild);
	}

	//-------
	//给li中设置子标签
	li.innerHTML = "<h3>" + title + "</h3><p>" + content + "</p><button class='delete-btn'>删除</btn>";

	//---------------大坑-----------------------
	//一定要把删除留言事件  放在此处设置
	//因为必须是先添加了留言  才创建里button标签
	//注意!!!querySelector() 每次只会查找符合条件的第一个标签
	deleteBtn = document.querySelector(".delete-btn");
	
	deleteBtn.onclick = function(){
		//点击删除按钮  删除的是所在的li
		console.log(this.parentElement);
		this.parentElement.remove();//remove() 删除自己
	}	
}


```
html样式:
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
<script src="js/01留言板.js" type="text/javascript" charset="utf-8"></script>
```
运行结果:
![](https://img-blog.csdnimg.cn/8219bcb8d4bb42a28a66470984c5aa09.png)
![](https://img-blog.csdnimg.cn/087505d8ddf44c649b1bc13dabee8d01.png)
