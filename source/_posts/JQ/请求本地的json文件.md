---
title: 请求本地的json文件
date: 2021-1-9 10:10:10
tags:
  - JQ
categories:
  - JQ
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
			.root{
				width: 800px;
				margin: 30px auto;
				border: 2px solid gold;
			}
			ul{
				list-style: none;
				width: 100%;
				display: flex;
				flex-wrap: wrap;
/*				justify-content: space-between;
*/			}
			h3{
				width: 97%;
				height: 40px;
				line-height: 40px;
				padding-left: 3%;
			}
			li{
				width: 10%;
				height: 40px;
				line-height: 40px;
				text-align: center;
				overflow: hidden;
				/*怪异盒模型*/
				box-sizing: border-box;
				border:1px solid gold;
			}
		</style>
	</head>
	<body>
		<div class="root">
			
		</div>
	</body>
</html>

<script src="js/jquery-3.5.1.js" type="text/javascript" charset="utf-8"></script>

<script type="text/javascript">
	//1.声明请求对象
	var request;
	//2.获取的请求对象---兼容写法   null也是false
	if(window.XMLHttpRequest){
		request = new XMLHttpRequest();
	}else{
		//主要为了兼容IE浏览器
		request = new ActiveXObject("Microsoft.XMLHTTP");
	}
	//3.设置本地文件的请求地址   可以是网址(即网络请求)  也可以是本地文件地址,例如 .jpg .png .txt .json等文件  (即本地请求)
	//参数1:请求方式 默认GET,也可以是POST,具体看接口文档
	//参数2:地址
	//参数3:是否开启异步请求
	 request.open("GET", "city.json", true);
	 
	 request.onreadystatechange = function(){
	 	if(request.readyState == 4 && (request.status == 200)){
	 		//能执行此处 说明请求加载完毕  并且数据请求成功
	 		//就能获取数据啦!! request.responseText就是请求到的数据
//	 		console.log(request.responseText);
	 		getDataByJSONString(request.responseText);
	 		
	 	}
	 }
	 
	 //最后一步  发送
	 request.send();
	 
	 //----------------------------------------------------
	 //封装解析数据的方法 
	 function getDataByJSONString(jsonStr){
	 	//1.解析
	 	var bigObject = JSON.parse(jsonStr);
	 	//2.获取所有的key
	 	var allKeyArray = Object.keys(bigObject);
	   //3.对所有的key 做升序
	    allKeyArray.sort();
	    //4.遍历数组  得到每一个key  来获取大对象中key对应的数组
	    for(var i in allKeyArray){
	    	var k = allKeyArray[i];
	    	//然后取出字母对应的数组
	    	var cityArray = bigObject[k];
	    	
	    	//每次得到新的字母 就创建ul标签  
	    	var ul = document.createElement("ul");
	    	$(".root").append(ul);
	    	//创建h3
	    	var h3 = document.createElement("h3");
	    	$(h3).html(k);
	    	$(ul).append(h3);
	    	
	    	//循环城市数组  得到每一个城市对象
	    	for(var j in cityArray){
	    		var cityObj = cityArray[j];
	    		var li = document.createElement("li");
	    		$(li).html(cityObj.name);
	    		$(ul).append(li);
	    		
	    		
	    	}
	    }
	 	
	 	
	 	
	 }
	 
	
</script>

```
![](https://img-blog.csdnimg.cn/0285495cb5184d419a9e40dce91d2245.png)
