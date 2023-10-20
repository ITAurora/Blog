---
title: jq中相关位置的属性
date: 2021-1-2 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/8.jpg
banner_img: ../articleImages/8.jpg
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
			body{
				height: 2000px;
			}
			#root{
				width: 300px;
				height: 100px;
				background-color: sandybrown;
				margin: 50px;
				position: relative;
				overflow: hidden;
			}
			#div1{
				width: 200px;
				height: 200px;
				background-color: yellowgreen;
				position: absolute;
				left: 30px;
				top: 40px;
				padding: 20px;
				border:5px solid skyblue;
				margin: 10px;
			}
			
			
			
		</style>
		
	</head>
	<body>
		<div id="root">
		<div id="div1">jq中跟位置相关的属性</div>		
		<img src="img/t1.png"/>
		</div>
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>
<script type="text/javascript">
	/*
	 跟尺寸相关的方法:
	 width()   获取/设置 标签宽度 width
	 innerWidth()  获取内尺寸,width + padding
	 outerWidth()  获取外尺寸 width + padding + border
	 outerWidth(true) 获取盒模型尺寸  width + padding + border + margin
	 
	 height()  获取/设置 标签的高度
	 innerHeight()  获取内尺寸,height + padding
	 outerHeight()  获取外尺寸 height + padding + border
	 outerHeight(true) 获取盒模型尺寸  height + padding + border + margin
	*/
	//测试
	console.log($("#div1").width());
	console.log($("#div1").innerWidth());
	console.log($("#div1").outerWidth());
	console.log($("#div1").outerWidth(true));
	//只有width()/height()   也可以重新设置标签的宽度/高度
	$("#div1").width(100);//数字类型 无需设置单位 jq中常常忽略单位px
	
	//--------------------------------------------------------------------
	/*
	 跟标签位置相关的尺寸:
	 offset()  获取 或者 设置 元素相对于窗口(包含滚动区域)的位置        类似page
	 position() 只能获取元素到离他最近的定位父级元素的位置
	 scrollTop() 获取垂直滚动条的滚动距离, 参数可选 不设置参数是获取值; 设置参数是修改值
	 scrollLeft() 获取水平滚动条的滚动距离,参数可选  同上
	 */
	
	//1.测试offset()   包含两个属性 offset().left  和   offset().top
	console.log("div1距离窗口左边", $("#div1").offset().left);
	console.log("div1距离窗口上面", $("#div1").offset().top);
	//也可以赋值操作
	$("#root").offset({
		left:100,
		top:100
	});
	
	//------------------------
	//2.测试position() 是参考定位的父标签  给left赋值用css("left", "");
	console.log($("#div1").position());
	console.log($("#div1").position().left); //取值是number类型的
	console.log($("#div1").position().top);
	
	//--------------------------------------------
	//3.测试scrollTop()/scrollLeft()  其实就是js中的内容区域滚动; 就是父标签太小,但是内容太大需要滚动才能看到所有的内容!!  可取值可赋值
	$("#root").scrollLeft(500); //内容区域向左滚动
	$("#root").scrollTop(300); //内容区域向上滚动
	//这还是我们js中讲过的那两个属性!  jq中并没重新设置这一对属性!!
	
	
</script> 
```
![](https://img-blog.csdnimg.cn/79817aa205404117a327e9c667b90b70.png)
