---
title: js中封装cookie操作方法并调用
date: 2020-12-14 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/5.jpg
banner_img: ../articleImages/5.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

js代码
```js
//方法1，判断cookie中是否有此属性(也就是key的位置)有的话返回true否则false
function hasKey(name){
	//1.获取所有cookie的数据 并且以;分割 成数组
	var strArray=document.cookie.split(";");
	//2.遍历数组 查看=号前面的属性名
	for(var i=0;i<strArray.length;i++){
		//再通过=分割成小数组
		var smallArray=strArray[i].split("=");
		//注意判断 属性名要去首尾空格
		if(smallArray[0].trim()==name){
			//说明存在
			return true;
		}
	}
	//如果代码执行到这里 说明name不在cookie中
	return false;
}
//方法2，通过属性名 查找属性值 可以搭配方法1一起用
function getValueByName(name){
	//1.获取所有cookie的数据 并且以;分割 成数组
	var strArray=document.cookie.split(";");
	//2.遍历数组 查看=号后面的属性值
	for(var i=0;i<strArray.length;i++){
		//再通过=分割成小数组
		var smallArray=strArray[i].split("=");
		//注意判断 值要去首尾空格
		if(smallArray[0].trim()==name){
			//说明存在 返回name所对应的值
			return smallArray[1];
		}
	}
	//如果代码执行到这里 说明name不在cookie中
}
//方法3，添加键值对 给cookie中存值（有参数（属性名，属性值，时间），无返回值的函数）
function addCookie(name,value,time){
	if(typeof time=="number"){
		//max-age 是数字类型 以秒为单位
		document.cookie=name+"="+value+";max-age"+time;
	}else{
		//expires是识别 事件字符串
		document.cookie=name+"="+value+";expires"+time.toString();
	}
	//time参数 只可以赋值秒数字或者date类型的日期对象
}
//方法4，删除cookie 其实设置为过去的时间 失效就是删除
function removeCookie(name){
	document.cookie=name+"=;max-age=-1";
}
```
html代码

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		
	</body>
</html>
<!--先引用js第三方库-->
<script src="js/封装cookie函数.js" type="text/javascript" charset="utf-8"></script>
<script type="text/javascript">
//	var t1 = 60*60*24;
//	document.cookie="username=wen;max-age=" + t1;
//	document.cookie="passwd=123456;max-age=" + t1;
//	document.cookie="phone=12345678910;max-age=" + t1;
//	var str=document.cookie;
//	var arr=document.cookie.split(";");
//	var phone=arr[2];
//	console.log(str);
//	console.log(arr);
//	console.log(phone);
//	var arr1=phone.split("=");
//	console.log(arr1);
//	console.log(arr1[1]);
    //使用封装好的方法测试
    
	console.log(hasKey("passwd"));
	//查询数据
	console.log(getValueByName("phone"));
	
</script>
```
![](https://img-blog.csdnimg.cn/8e8bd321b4e7431e9985e3aaaa390c00.png)
![](https://img-blog.csdnimg.cn/9e6a5b61c5d94125824a33b50f1a6537.png)
