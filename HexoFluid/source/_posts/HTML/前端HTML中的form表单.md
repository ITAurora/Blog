---
title: 前端HTML中的form表单
date: 2020-10-18 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/17.jpg
banner_img: ../articleImages/17.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
	</head>
	<body>
		<!--<a href="http://www.baidu.com/s?wd=黄景瑜">百度一下</a>-->
		<!--
			form的属性解释:
			action  设置要提交的链接
			method  发起请求的方式,默认是get 也可以是post.具体要看后台对此链接请求的设置!
			form中最关键的标签---input 输入框系列
			input中属性的解释:
			type   决定input的样子,通过切换类型值来决定输入框的功能
			name  就是提交链接时, ?问号后面的参数名 例如 wd=xxx的wd参数名  就是name属性决定的
			value   输入框的默认值
			placeholder  水印字,提示性文字
			required   必填不能为空
			checked   默认选中,适用于单选框和复选框.
		-->
		<form action="测试测试.html" method="get">
			<!--普通输入框  -->
			<span>账号:</span>
			<input type="text" name="username" required/>
			<br /><br />
			<!--密码型输入框   圆点密文-->
			<span>密码:</span>
			<input type="password" name="passwd" placeholder="请输入密码" required="required"/>
			<br /><br />
			<!--单选框-->
			<span>性别:</span>
			<input type="radio" name="sss" value="男" checked  />男
			<input type="radio" name="sss" value="女"/>女
			<!--name决定链接中的参数名  
				value决定提交的数据
			-->
			<br /><br />
			<!--复选框-->
			<span>爱好:</span>
			<input type="checkbox" name="hobby" value="唱"  checked="checked" />唱
			<input type="checkbox" name="hobby" value="跳"/>跳
			<input type="checkbox" name="hobby" value="rap" checked   />rap
			<input type="checkbox" name="hobby" value="篮球">篮球
			<br /><br />
			<!--数字选框-->
			<span>年龄:</span>
			<input type="number" name="age"/>
			<!-- e 是自然数-->
			<br /><br />
			<!--邮箱选款 要求复合邮箱的格式-->
			<span>邮箱:</span>
			<input type="email"/>
			<br /><br />
			<!--文件选框-->
			<span>附件:</span>
			<input type="file" />
			<br /><br />
			<!--文件肯定不能带入链接参数,将来需要学习上传文件功能  视频音频图片文件 等都需要上传服务器-->
			<!--以下两个常用-->
			<!--文本域   就是会自动换行的长内容输入
				rows 行数   cols列数   通过这两个属性来控制宽高
			-->
			<textarea name="liuyan" rows="10" cols="30">内容写在这就可以啦</textarea>
			<br /><br />
			<!--下拉框 selected默认选中  仅仅适用于下拉框-->
			<span>城市:</span>
			<select name="city">
				<option value="郑州">郑州</option>
				<option value="杭州" selected>杭州</option>
				<option value="广州">广州</option>
				<option value="福州">福州</option>
				<option value="泉州">泉州</option>
				<option value="徐州">徐州</option>
			</select>
			<br /><br />
			<!--颜色选框-->
			<input type="color" />
			<br />
			<!--日期选款  date  datetime-->
			<input type="datetime" />
			<br />
			<!--滑动条
				min 最小值  max最大值 value当前值
			-->
			<input type="range" max="100" min="20" value="50"/>
			<br />
			<!--链接选框  网址格式-->
			
			<input type="url" value="这是;链接url框"/>
			<br />
			<!--隐藏域  就是隐藏状态的选框 常用来传递一些不需要用于输入  但是又需要传给服务器的参数值  -->
			<input type="hidden" name="id" value="1"/>
			<br />
			
			<!--按钮系列
				submit  提交按钮,一旦点击立马进行form标签请求
				reset  重置按钮,清空数据
				button  普通按钮,无效果,需要搭配js
			-->
			<input type="submit" value="提交"/>
			<input type="reset" value="重置"/>
			<input type="button" value="普通按钮"/>
			<button>普通按钮</button>
		</form>
	</body>
</html>

```
运行结果：
![](https://img-blog.csdnimg.cn/5820ac600835489b9af14593cd244b84.png)

