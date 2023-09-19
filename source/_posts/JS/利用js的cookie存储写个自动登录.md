---
title: 利用js的cookie存储写个自动登录
date: 2020-12-15 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/8.jpg
banner_img: ../articleImages/8.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

登录界面
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
				background-color: #f2f2f2;
			}
			ul{
				list-style: none;
				width: 400px;
				padding: 20px;
				margin: 30px auto;
				background-color: white;
				border-radius: 8px;
			}
			.c1{
				width: 400px;
				height: 40px;
			}
			li{
				margin-bottom: 20px;
			}
			
		</style>
	</head>
	<body>
		<ul>
			<li>		
				<input type="text" placeholder="请输入手机号" class="c1"/>
            </li>
			<li>
				<input type="password" placeholder="请输入密码6-16位数字,字母_组合"  class="c1"/>
			</li>
			<li>
				<input type="button" value="登录"  class="c1"/>
			</li>
		</ul>
	</body>
</html>

<script src="js/cookie.js" type="text/javascript" charset="utf-8"></script>
<script type="text/javascript">
	
	var phoneEl = document.querySelector("li:first-child input");
	var passwdEl = document.querySelector("li:nth-child(2) input");
	var loginBtn = document.querySelector("li:last-child input");
	//---------------------
	//登录状态  再执行下面代码之前  先进入cookie查看登录状态
	var loginState = getValueByName("loginState");
	if(loginState == "200"){
		//说明你曾经已经登陆成功过  那就无需登录 
		location.href = "05主页.html";
	}
	
	//点击事件
	loginBtn.onclick = function(){
		//判断账号密码 是否合法  才能进入主页!!
		var phone = phoneEl.value;
		var passwd = passwdEl.value;
		var r1 = /^1[3-9]\d{9}$/;
		var r2 = /^[a-zA-Z]\w{5,15}$/;
		
		if(r1.test(phone) && r2.test(passwd)){

        // 将登录状态存储到本地 下次在进入登录页 就会直接进入主页 无需输入账号密码
		// 3天  60 * 60 * 24 * 3   你可以先写1分钟 做测试!!!
			addCookie("loginState", "200", 60);
			//恭喜你 可以登录 就是进入主页
			location.href = "05主页.html";
		}
		
	}
	
	
</script>

```
跳转界面

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<h1 style="background-color: salmon;">主页</h1>
	</body>
</html>
<script src="js/cookie.js" type="text/javascript" charset="utf-8"></script>

<script type="text/javascript">
	//如果你直接运行此页面 那要看你的登录状态是否在有效期内
	var loginState = getValueByName("loginState");
	if(loginState != "200"){
		//就说明 没登录 你得先去登录页面
		location.href = "04登录.html";
	}
	
</script>

```
js代码

```js
//2.通过属性名 查找属性值  可以搭配方法1 一起使用!!!!!!!!!!
function getValueByName(name){
	//1.获取所有cookie的键值对 数组
	var strArray = document.cookie.split(";");
	//2.循环遍历
	for(var i = 0; i < strArray.length; i++){
		var smallArray = strArray[i].split("=");
		if(smallArray[0].trim() == name){
			return smallArray[1];
		}
	}
	//如果代码执行到此处 说明name不存在!!
}
```
![](https://img-blog.csdnimg.cn/970096ed51cf479e867e267ad3809003.png)
![](https://img-blog.csdnimg.cn/c427c7141f5c457a98eda384162010f7.png)
![](https://img-blog.csdnimg.cn/6340fa26cb4b49b5bad49ceeba3915bb.png)
再次运行会自动进入到此页面不用再次登录
![](https://img-blog.csdnimg.cn/055e31dd6d1a4cddbae016e908246971.png)
