---
title: 利用js实现自定义滚动条
date: 2020-12-07 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/16.jpg
banner_img: ../articleImages/16.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>自定义滚动条</title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			#box{
				width: 300px;
				height: 530px;
				margin: 40px auto;
				position: relative;
				/*溢出隐藏*/
				overflow: hidden;
				/*不进行js自定义设置也可以做到滑动条如下两者搭配使用*/
				/*overflow: hidden;
				overflow-y: scroll;*/
			}
			/*内容*/
			#content{
				width:285px;
				position: absolute;
				left: 0;
				top: 0;
				font-size: 20px;
			}
			/*滑动条下面的浅灰色*/
			#slide-box{
				width: 15px;
				height: 530px;
				position: absolute;
				top: 0;
				right: 0;
				background-color: gainsboro;
			}
			#slide{
				width: 15px;
				/*高度不能写 因为要参考具体内容的大小*/
				/*height: 30px;*/
				background-color: gray;
				position: absolute;
				top:0;
				left:0;
				border-radius: 7.5px;
			}
			
			
			
		</style>
	</head>
	<body>
		<div id="box">
			<!--内容区域-->
			<div id="content">
				　内容区域

			</div>
		
		  <!--模仿滑动条-->
		  <div id="slide-box">
		  	<div id="slide"></div>
		  </div>
		</div>
	</body>
</html>
<script type="text/javascript">
	//查找标签
	var slideBox = document.querySelector("#slide-box");
	//按照比例设置滚动条的高度
	slide.style.height = box.offsetHeight / content.offsetHeight * slideBox.offsetHeight + "px";
	
	
	
	//给box添加滚轮事件
	box.onmousewheel = function(){
		if(event.wheelDelta > 0){
			//滚轮向下滚动   看下面的内容
			content.style.top = content.offsetTop + 20 + "px";
			//注意 top值最大就是0 因为运行结束,顶部的就是新闻的第一行!!
			//往上走是负值   往下才是正值!!! 其实一直都是负的top值 到 0 
		    if (content.offsetTop >= 0) {
		    	content.style.top = "0px";
		    }
		    //修改滚动条的位置
		    slide.style.top = -(content.offsetTop / content.offsetHeight) * slideBox.offsetHeight + "px";
		}else{
			//滚轮向上  看上面的内容
			content.style.top = content.offsetTop - 20 + "px";
			//设置最小top值!!
			if(content.offsetTop <=box.offsetHeight - content.offsetHeight){
				content.style.top = box.offsetHeight - content.offsetHeight + "px";
			}
			 //修改滚动条的位置
		    slide.style.top = -(content.offsetTop / content.offsetHeight) * slideBox.offsetHeight + "px";
		}
	}
	
	
	//滚动条 按下可以滑动
	slide.onmousedown = function(){
		//获取滑动条静止的时候 距离浏览器窗口顶部的位置
		var t = event.clientY - this.offsetTop;
		slideBox.onmousemove = function(){
			slide.style.top = event.clientY - t + "px";
			//设置界限  上下不能滑出父标签范围
			if(slide.offsetTop <= 0){
				slide.style.top = "0px";
			}
			if(slide.offsetTop > slideBox.clientHeight - slide.offsetHeight){
				slide.style.top = slideBox.clientHeight - slide.offsetHeight + "px";
			}
			//修改内容的top值
			content.style.top = - slide.offsetTop / slideBox.offsetHeight * content.offsetHeight + "px";
		}
	}
	//鼠标抬起  滑块结束滑动
	slide.onmouseup = function(){
		slideBox.onmousemove = null;
	}
	
</script>
```