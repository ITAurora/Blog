---
title: js实现放大镜效果
date: 2020-12-07 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/15.jpg
banner_img: ../articleImages/15.jpg
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
			/*最后一个坑*/
		html, body{
			width: 100%;
			height: 3000px;
		}
			
			#small{
				width: 300px;
				height: 300px;
				border: 5px solid gold;
				position: relative;
				float: left;
				margin: 100px;
			}
			#small img{
				width: 300px;
			}
			#zoom{
				width: 100px;
				height: 100px;
				background-color: rgba(0,0,0,0.5);
				position: absolute;
				left: 0;
				top:0;
				/*默认隐藏*/
				display: none;
			}
			/*-----------------*/
			#big{
				width: 300px;
				height: 300px;
				float: left;
				margin: 100px;
				border: #FFD700 4px solid;
				overflow: hidden;
				display: none;
				
			}
			#big img{
				width: 900px;
			}
			
			
		</style>
	</head>
	<body>
		<!--原图div-->
		<div id="small">
			<img src="img/600.jpg"/>
			<!--悬浮层 充当放大的选中区域-->
			<div id="zoom"></div>
		</div>
		
		<!--放大区域-->
		<div id="big">
			<img src="img/600.jpg"/>
		</div>
		
	</body>
</html>
<script type="text/javascript">
	/*
	 放大镜效果技巧, 悬浮层100 : 原图300  =====  原图300 : 放大之后的图900
	 */
	
	//鼠标进入small的是  显示悬浮层 显示大图
	small.onmouseenter = function(){
		zoom.style.display = "block";
		big.style.display = "block";
	}
	//鼠标离开 重新隐藏
	small.onmouseleave = function(){
		zoom.style.display = "none";
//		big.style.display = "none";
	}
	
	//鼠标移动   注意 悬浮层跟着鼠标移动
	small.onmousemove = function(){
		//让鼠标的位置   在悬浮层的中心上
		//最佳选择!!!!!!!!page
		var l = event.pageX - this.offsetLeft - this.clientLeft - zoom.offsetWidth / 2;
		var t = event.pageY - this.offsetTop - this.clientTop - zoom.offsetHeight / 2;
      //设置放大镜可移动的范围  不能出去
      if(l <= 0){
      	
      	l = 0;
      }
      //最大left值
      if(l >= small.clientWidth - zoom.offsetWidth){
      	l = small.clientWidth - zoom.offsetWidth;
      }
      
      //最小top是 0
      if(t <= 0){
      	t = 0;
      }
      //最大top值
      if(t >= small.clientHeight - zoom.offsetHeight){
      	t =  small.clientHeight - zoom.offsetHeight;
      }
		zoom.style.left = l + "px";
	    zoom.style.top = t + "px";
	    //-------------------------------------------
	    
	    //修改大图的位置!!
	    /*
	     悬浮层当前位置 (可知) / 悬浮层可移动的范围(可知)   ============
	     大图显示的位置(未知,要算出开的) / 大图可滚动的总范围(可知)
	      
	      如果不会算,那以后你就用技巧  让他们比例都一样!!
	    那么大图的位置, 就是悬浮层的位置  * 比例值!!!!
	    */
	   //scrollTop属性  是让自己的内容区域滚动
	    big.scrollLeft = l * 3;
	    big.scrollTop = t * 3;
	}
</script>
```
![](https://img-blog.csdnimg.cn/fc4c70aeafeb42a48d68c61ac0e31e58.png)
![](https://img-blog.csdnimg.cn/a28d2dad95994088940bf17f6d77bfa2.png)
