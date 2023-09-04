---
title: 前端HTML新特性
date: 2020-10-21 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
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
	</head>
	<body>
		<!--
			HTML5新特性
			1.新增了新标签
			2.支持本地存储
			3.新增了音频视频标签
			4.新增了canvas画图标签
			HTML5的新特性目前只有在标准浏览器下支持
		-->
		<!--1.mark标签 双标签 标记标签-->
		<p>123<mark>456</mark>789</p>
		<!--2.meter标签 双标签 
			一般表示电量或者内存的使用情况
			meter 里面内容只会当浏览器不支持此标签时才会显示
		所以一般是给用户做提示用的
		
			value 当前值
			max 最大值
			min 最小值
			low 最低预警值
			high 最高预警值
		-->
		<meter max="100" min="0" value="70" low="20" high="80">此浏览器不知此标签</meter>
		<!--3.拼音标注标签
			ruby标签 需要rt和rb标签结合使用
			把需要标注的内容写在ruby中
			把标注的内如写在rt中
			当浏览器不支持此标签时 才会执行rp中的内容
		-->
		<br />
		<ruby>	
		<rt>123456789987654321</rt>
		<rp>此标签浏览器不支持</rp>
		</ruby>
		<br />
		<ruby>
			中华人民共和国
			<rt>zhonghuarenmingongheguo</rt>
		</ruby>
		<!--4.datalist标签 双标签 需要结合input使用
			输入框inpt如果想要与datalist建立连接，需要先给datalist设置
			唯一表示 然后用input的list属性去关联datalist的id属性
			
		-->
		<form action="">
			<input type="text" placeholder="请输入城市名"  list="city"/>
			<datalist id="city">
				<option >北京</option>
				<option >上海</option>
				<option >广州</option>
				<option >福州</option>
			</datalist>
			<input type="submit" value="提交" />
		</form>
		<!--5.datails标签 双标签 自带折叠效果 需要与summary结合使用
			summary是datalis的标题 两者不可分割
			折叠内容是可以任意类型的标签
			
		-->
		<details>
			<summary style="list-style: none;">这是折叠效果</summary>
			<p>123456789</p>
		</details>
		
		<img src=""/>
		<!--6.音频标签 audio双标签 支持mp3 ogg wav等格式
			常用属性：
			controls 控制面板 用来显示进度条 音量等
			autoplay 自动播放
			loop 是否循环播放
			muted 是否静音
			
		-->
		<br />
		<audio src="img/Nike - DuskTillDawn.mp3" controls="" autoplay="" loop="loop" muted="muted"></audio>
		<!--7.视频标签 video 双标签 支持mp4 ogg webm格式
			source标签 解决不同浏览器因为版本不同支持的文件格式差异问题
		-->
		<br />
		<video width="300px" height="300px" controls="controls" loop="loop">
			<source src="img/视频素材.mp4" type="video/mp4"></source>
			<source src="img/视频素材.ogv" type="video/ogg"></source>
			<source src="img/视频素材.webm" type="video/webm"></source>
			<object width="" height="" type="application/x-shockwave-flash" data="myvideo.swf">
				<param name="movie" value="myvideo.swf" />
				<param name="flashvars" value="autostart=true&amp;file=myvideo.swf" />
			</object>
			当前浏览器不支持 video直接播放，点击这里下载视频： <a href="myvideo.webm">下载视频</a>
		</video>
		<br />
		<audio src="img/Nike - DuskTillDawn.mp3" controls="" autoplay="" loop="loop" muted="muted"></audio>
		<br />
		<!---------------------------------------------->
		<!--8.重点-语义标签-->
		<header>块元素头部内容设置</header>
		<section>尽可能写成模块化设置</section>
		<footer>尾巴也是块元素</footer>
		<!--9.input标签的新特性-->
		<!--必填属性-->
		<input type="text" required/>
		<!--自动获取焦点-->
		<br />
		<input type="text" autofocus="autofocus"/>
		
		
	</body>
	
</html>

```
运行结构：
![](https://img-blog.csdnimg.cn/07df26e3c958455c8a6d5372991b9000.png)
