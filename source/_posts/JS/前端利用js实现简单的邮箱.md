---
title: 前端利用js实现简单的邮箱
date: 2020-11-17 12:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/2.jpg
banner_img: ../articleImages/2.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			
			ul{
				list-style: none;
			}
			
			.root{
				width: 500px;
				height: 400px;
				border: #FFD700 2px solid ;
				margin: 30px auto;
			}
			.email{
				width: 100px;
				height: 100%;
				float: left;
				background-color: pink;
				position: relative;
			}
			
			.email li{
				width: 100%;
				height: 100px;
				line-height: 100px;
				text-align: center;
				border-bottom: #FFD700 solid 2px ;
				box-sizing: border-box;
			}
			.email li:last-of-type{
				border-bottom: none;
			}
			.email span{
				position: absolute;
				right: 0;
				top: 25px;
				width: 0px;
				height: 0px;
				display: inline-block;
				border:25px solid transparent;
				border-right-color: red;
				transition: all .3s linear;
			}
			/*---------------------*/
			.right{
				float: right;
				width: 400px;
				height: 100%;
				background-color: orange;
				font-size: 32px;
				text-align: center;
				line-height: 400px;
			}
			
			
			
		</style>
	</head>
	<body>
		<div class="root">
			<ul class="email">
				<li>QQ邮箱</li>
				<li>网易邮箱</li>
				<li>新浪邮箱</li>
				<li>阿里邮箱</li>
				<span id="sanjiao"></span>
			</ul>
			<div class="right">这是QQ邮箱</div>
		</div>
	</body>
</html>

<script type="text/javascript">
	//1.获取标签
	var liArray = document.getElementsByTagName("li");
	//右边的div
	var rightDiv = document.getElementsByClassName("right")[0];
	
	//2.变量
	var colorArray = ["orange", "purple", "greenyellow", "skyblue"];
	
	//3.函数事件  index中文 下标
	for (var i = 0; i < liArray.length; i++) {
      liArray[i].index = i;
      liArray[i].onmouseenter = function(){
      	//1.修改三角形的位置
      	sanjiao.style.top = 25 + 100 * this.index + "px";
      	//2.修改文字
      	rightDiv.innerHTML = "这是" + this.innerHTML;
      	//3.修改背景颜色
      	rightDiv.style.backgroundColor = colorArray[this.index];
      }
	}
	
	
</script>

```
运行结果:
![](https://img-blog.csdnimg.cn/533cc5e5b34148ab87cb22b305dbea58.png)
鼠标放上去：
![](https://img-blog.csdnimg.cn/75127567961c42409f0689964c2f4338.png)
