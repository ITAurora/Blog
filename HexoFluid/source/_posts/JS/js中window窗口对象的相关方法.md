---
title: js中window窗口对象的相关方法
date: 2020-11-25 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
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
		<style type="text/css">
			body{
				width: 4000px;
				height: 3000px;
				padding-top: 500px;
			}
		</style>
	</head>
	<body>
		<input type="button" value="打开网页" id="open"/>
		<input type="button" value="关闭网页" id="close"/>
		<!---------------------------------------------------->
		<input type="button" value="moveTo" id="to"/>
		<input type="button" value="moveBy" id="by"/>
        <input type="button" value="resizeTo" id="sizeTo"/>
        <input type="button" value="resizeBy" id="sizeBy"/>
        <!--滚动-->
        <input type="button" value="scrollTo" id="sto"/>
        <input type="button" value="scrollBy" id="sby"/>
        
	</body>
</html>
<script type="text/javascript">
	//window窗口对象
	//新打开窗口
//	window.open(链接, 窗口名字类似做个标记, 窗口尺寸位置等参数);
	//新窗口的位置  是参考电脑屏幕进行设置的!!!
	
	var openEl = document.querySelector("#open");
	var closeEl = document.querySelector("#close");
	var newWindow = []; //null是对象类型  空对象  
    openEl.onclick = function(){
    	console.log("0000");
//  	 newWindow = window.open("http://www.baidu.com", "百度", "");
          for(var i = 0; i < 5; i++){
	          newWindow[i] = window.open("", i+"", "width=400, height=400, left=100, top=100");
         }
    		
    }
	
	 closeEl.onclick = function(){
	 	//新窗口.close()  就是关闭新窗口
//  		newWindow.close(); //关闭窗口!!!
         for(var i = 0; i < newWindow.length; i++){
            	newWindow[i].close();
            }
    }
	//---------------------------------------
	//移动窗口
	/*
	 moveTo(x, y) 移动到某个指定的位置,但是相对于整个窗口,无法超出屏幕!!
	 moveBy(x, y) 移动到某个位置,相对于自身所在位置再移动x y,无法超出屏幕!
	 */
	to.onclick = function(){
		newWindow[4].document.body.style.backgroundColor = "red";
		newWindow[4].moveTo(100, 200);//屏幕左上角原点
	}
	
	by.onclick = function(){
	newWindow[3].document.body.style.backgroundColor = "green";
	newWindow[3].moveBy(-100, 200);//参考自身原本的位置!!
	}
	
	//修改窗口大小
	/*
	 resizeTo(width, height) 窗口宽高增大/减小到width和height
	 resizeBy(width, height) 窗口宽高在原本尺寸的基础上再增大/减小width和height
	 */
	sizeTo.onclick =  function(){
		newWindow[4].resizeTo(200, 300);
	}
	
	sizeBy.onclick = function(){
		newWindow[4].resizeBy(-200, -100);
		
	}

    /*
       设置窗口的滚动  (更不常用)  这两个方法使用前提是页面支持滚动!!!!
    1.scorllTo(x, y) 设置对应窗口的滚动条的位置,x水平滚动条的位置,y竖直方向滚动条的位置
    2.scrollBy(x, y) 设置对应窗口的滚动条位置,by 都只在原本滚动的基础之上再滚动x y距离!!
    */
	
	sto.onclick = function(){
		//用的是当前网页所在的窗口
		window.scrollTo(400, 300);
	}
	
	
	sby.onclick = function(){
	  window.scrollBy(0, 150);
	}
	
	
</script>

```
运行结果:
功能自行测试
![](https://img-blog.csdnimg.cn/459f056a0b0646c1a74691a6bece33c7.png)
