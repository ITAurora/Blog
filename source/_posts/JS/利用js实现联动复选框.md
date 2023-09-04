---
title: 利用js实现联动复选框
date: 2020-11-23 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/14.jpg
banner_img: ../articleImages/14.jpg
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
		<!--省份-->
		<select id="sheng">
			<option value="省份">省份</option>
			<option value="河南省">河南省</option>
			<option value="浙江省">浙江省</option>
		</select>
		<!--城市-->
		<select id="city">
			<option value="市区">市区</option>
		</select>
		
	</body>
</html>

<script type="text/javascript">
	//1.获取标签
	//2.定义变量
	var arr1 = ["郑州市", "洛阳市", "驻马店市", "焦作市", "南阳市", "新乡市", "开封市", "漯河市", "濮阳市", "安阳市"];
	var arr2 = ["杭州市", "金华市", "义乌市", "温州市", "绍兴市", "宁波市", "嘉兴市"];
	
	//3.select的事件 onchange 也就是只有值变化 才会执行!
	sheng.onchange = function(){
		//方式1:简单暴力又好用
//		city.innerHTML = "";//清空子标签内容
		//方式2: city标签中的子标签是数组容器
//		for(var i = 0; i < city.children.length; i++){
//			city.children[i].remove();
//			i--;
//		}
		// [1, 2, 3, 4, 5, 6]
		//方式3:
		var l = city.children.length;
		for(var i = 0; i < l; i++){
			city.children[0].remove();
		}
		//问题在于  i++一直在自增; 
		//city.children.length 这个值一直在减小!!
		
		
		
		// firstElementChild 要保证,其不能为空!!
		//注意   程序不允许  undefined.语法  也不允许null.语法
		//只有真实有效的对象可以点语法操作!
		
		//定义一数组  来接收应该显示的市区数组
		var tempArray = ["市区"];
		if(this.value == "河南省"){
			tempArray = arr1;
		}
		
		if(this.value == "浙江省"){
		  tempArray = arr2;
		}
		//--------------------------------
		for(var i = 0; i < tempArray.length; i++){
			var option1 = document.createElement("option");
			option1.innerHTML = tempArray[i];
			option1.value = tempArray[i];
			city.appendChild(option1);
		}
		console.log(tempArray);
	}
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/18adf98828264331839f7537edfbabe9.png)
![](https://img-blog.csdnimg.cn/8500ea743ede44c0833c42cfd5f25928.png)
