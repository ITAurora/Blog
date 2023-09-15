---
title: js中cookie存储的使用
date: 2020-12-11 10:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/3.jpg
banner_img: ../articleImages/3.jpg
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
	</body>
</html>
<script type="text/javascript">
	
	/*
	 cookie的概念:
	 cookie的本质上是一段文本信息,存储本地浏览器中,而且可以跟随网络请求在本地与服务器之间传递(服务器后面node会讲解).当某个网站能买到对应请求的cookie信息,就可以根据信息对用户的行为或者偏好设置做出反馈!
	 cookie的适用场景:
	 1.保存用户的登录状态
	 2.存储购物车信息等
	 3.跟踪用户行为,进行个性化网页定制
	 
	 cookie的弊端:
	 1.容量小 大约4kb
	 2.cookie可以手动删除(非代码行操作删除)
	 3.限时存储,要设置存储时间限制!! 
	 */
	
	
	//方式1:
	console.log(document.cookie);//cookie本质 你看到啦!就是一个字符串
	//max-age 以秒为单位,存储多长时间!! 
	//多少秒之后失效!!!
	//注意cookie的时间是以0时区的时间为标准的! 所以差8个小时!!!但是不影响使用!! 
	document.cookie = "name=lily;max-age=20";  //20秒之后就失效
	//3天后失效
	var time1 = 60 * 60 * 24 * 3;
	document.cookie = "passwd=123456;max-age=" + time1;
	
	//怎么删除呢?? 没有直接删除的方式  只能让它立刻失效就行
	//因为只要失效 就会自动删掉!!!
//	document.cookie = "passwd=123456;max-age=-1";
	
	
	//方式2:
	//expires 识别日期字符串
	//1天后失效
	var now = new Date();//获取此时此刻  是参考系统时间!!!
	var tomorrow = now.getDate() + 1; //天数+1
	now.setDate(tomorrow); //再把+1的后日期 重新设置
	///--------------------------------
	//1年后   
     //now.setFullYear(now.getFullYear() + 1);
     //20分钟后
//   now.setMinutes(now.getMinutes() + 20);
	document.cookie = "hobby=打代码;expires=" + now.toString();
	
	
</script>
```
![](https://img-blog.csdnimg.cn/123665f5515843069c7a0d93d62da5f5.png)
