---
title: 前端js实现全选反选
date: 2020-11-14 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/13.jpg
banner_img: ../articleImages/13.jpg
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
		<button id="all">全选</button>
		<button id="fan">反选</button>
		<input type="checkbox" id="i1"/>
		
		<ul>
			<li><input type="checkbox"/>洗jio</li>
			<li><input type="checkbox" />按摩</li>
			<li><input type="checkbox" />拔罐</li>
			<li><input type="checkbox" />刮痧</li>
			<li><input type="checkbox" />推背</li>
			<li><input type="checkbox" />马萨基</li>
			<li><input type="checkbox" />spa</li>
		</ul>
	</body>
</html>
<script type="text/javascript">
	var allCheckBox = document.getElementsByTagName("ul")[0].getElementsByTagName("input");
	
	
	
	//全选
	all.onclick = function(){
		for(var i = 0; i < allCheckBox.length; i++){
			allCheckBox[i].checked = true;
		}
		i1.checked = true;
	}
	
	//反选
	fan.onclick = function(){
		var count = 0;//计数
		for(var i = 0; i < allCheckBox.length; i++){
			//方式1
			/*
			if(allCheckBox[i].checked == true){
				allCheckBox[i].checked = false;
			}else{
				allCheckBox[i].checked = true;
			}
			*/
			//方式2
			allCheckBox[i].checked = !allCheckBox[i].checked;
		  
		  //判断每个选项是否为true 并计数!
		if(allCheckBox[i].checked == true){
			count++;
		}
	}
		//一定要在循环结束后
		if(count == allCheckBox.length){
			i1.checked = true
		}else{
			i1.checked = false;
		}
		
	}
	
	//点击分选项
	for(var i = 0; i < allCheckBox.length; i++){
		allCheckBox[i].onclick = function(){
			var count = 0;//计数
			for(var j = 0; j < allCheckBox.length; j++){
				if(allCheckBox[j].checked == true){
					count++;
				}
				
			}
			//循环结束  遍历一遍
			if(allCheckBox.length == count){
				i1.checked = true;
			}else{
				i1.checked = false;
			}
			
			
		}
	}
</script>

```
运行结果:
![](https://img-blog.csdnimg.cn/d2ba6bb3b7b24884924a5aab810a4ee3.png)
点击全选:
![](https://img-blog.csdnimg.cn/fd832a5b6b69411fbe5152972f3df494.png)

点击部分:
![](https://img-blog.csdnimg.cn/2bb4a197fb7f47bc8ce58149b235c5b6.png)
点击反选:
![](https://img-blog.csdnimg.cn/db3d733d664143259d07e42debf02832.png)

