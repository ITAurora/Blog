---
title: jq中利用元素关系查找标签
date: 2021-1-1 10:10:10
tags:
  - JQ
categories:
  - JQ
index_img: ../articleImages/7.jpg
banner_img: ../articleImages/7.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>关系型查找标签</title>
	</head>
	<body>
		<div id="div1">
			<div id="div2">
				<div id="div3">
					<div id="div4"></div>
					<div id="div5"></div>
					<div id="div6">
						<div id="div7"></div>
					</div>
				</div>
			</div>
		</div>
		
	</body>
</html>
<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>
<script type="text/javascript">
	/*
	元素之间的关系:
	1.父子
	2.兄弟
	利用元素关系查找标签
	*/
	//1.*******************查找父元素
	console.log($("#div6").parent());
	//2.查找一个元素的所有直系祖先元素	
	console.log($("#div6").parents());
	//3.查找一个元素的所有直系祖先元素,但是可以设置查找到哪个层级
	console.log($("#div6").parentsUntil("#div1"));
	//4.**************************查找元素的所有子元素   
	console.log($("#div3").children());
	//5.************************查找元素的所有后代元素  *是css中通配符 代表任意标签
	//find("选择器") 查找后代中的某一个标签!!!
	console.log($("#div1").find("#div6"));
	//6.查找上一个兄弟元素
	console.log("div6的上一个兄弟", $("#div6").prev());
	//7.查找一个标签上面所有的兄弟标签
	console.log("div6上面所有兄弟", $("#div6").prevAll());
	//  prevUntil("选择器") 查找到此标签上面哪个兄弟标签就停止
	//8. 查找下一个兄弟标签
	console.log("div4的下一个兄弟", $("#div4").next());
	//nextAll 查找以下 所有的兄弟标签
	console.log("div4以下所有兄弟", $("#div4").nextAll());
	// nextUntil() 找到哪个兄弟标签就停止
	//9.******************最常用  最好用!!! 查找除了本标签外的其他所有兄弟标签
	console.log($("#div5").siblings());
</script>
```
![](https://img-blog.csdnimg.cn/a9c037a303a54f9c90aa83eed25c9d3b.png)
