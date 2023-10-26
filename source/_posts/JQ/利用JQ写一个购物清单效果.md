---
title: 利用JQ写一个购物清单效果
date: 2021-1-6 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/12.jpg
banner_img: ../articleImages/12.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			.list{
				width: 450px;
				height: 200px;
				line-height: 200px;
				background-color: #333;
				margin: 30px auto;
				text-align: center;
			}
			h2{
				color: white;
				height: 200px;
			}
			ul{
				list-style: none;
			}
			li{
				color: white;
				height: 40px;
				line-height: 40px;
				background-color: brown;
				border-bottom: dimgray 2px solid;
			}
			
		</style>
	</head>
	<body>
		<div class="list">
			<h2>购物清单</h2>
			<ul class="goods">
				<li>蔬菜</li>
				<li>水果</li>
				<li>果冻</li>
				<li>坚果</li>
				<li>巧克力</li>
			</ul>
		</div>
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>
<script type="text/javascript">
	$(function(){
		//each()  就是jq版的for循环  是为了遍历$() 对象中的每一个标签
		$(".goods li").each(function(i){
			//$(this) 就是遍历得到的一个一个的标签对象
			//i就是下标
			//delay()  延时 单位毫秒
			$(this).hide().delay(i * 300).fadeIn(300);
		}).click(function(){
			$(this).animate({
				paddingLeft: 50,
				opacity:0
			},500,"linear",function(){
				//动画结束
				$(this).remove();
			})
		})
	})
	
	
	
</script>
```
![](https://img-blog.csdnimg.cn/fe010d6f6a1347e6a0b86b72a927e29f.png)
