---
title: 前端HTML transition过渡动画的使用
date: 2020-10-24 11:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/13.jpg
banner_img: ../articleImages/13.jpg
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
			.one{
				margin: 50px auto;
				width: 300px;
				height: 300px;
				background-color: pink;
				/*设置动画属性*/
				/*单属性支持多个属性用，隔开*/
				transition-property: width,height;
				/*设置动画时间*/
				transition-duration: 1s;
				/*设置动画速率*/
				transition-timing-function: linear;
				/*设置动画延时*/
				transition-delay: 0.5s;
				/*综合写法*/
				/*transition: all .5s linear;*/
			}
			.one:hover{
				width: 400px;
				height: 400px;
				opacity: 0.5;
			}
			input:first-of-type{
				width: 300px;/*需要初始化才能使transition生效*/
				height: 30px;
				outline: none;
				border: solid 5px red;
				transition: all .5s linear;
			}
			/*焦点选择器*/
			input:first-of-type:focus{
				width: 600px;
				height: 60px;
				background-color: pink;
				border-color: yellow;
			}
			input:last-of-type{
				transition: all .5s linear;
				position: relative;
				top: 0;
			}
			/*checked选中*/
			input:last-of-type:checked{
				/*margin-top: 200px;*/
				top: 200px;
			}
			/*----------------------------*/
			/*媒介触发动画*/
			@media only screen and (max-width: 1300px) {
				.one{
					background-color: red;
				}
			}
		</style>
	</head>
	<body>
		<div class="one"></div>
		<input type="text" />
		<input type="checkbox" />
	</body>
</html>
<!--过渡动画
	1.需要触发才会执行 例如hover focus js @media等
	2.过渡动画没有动画次数 一触发就执行一次
	3.
-->
```
运行结果：
初始界面
![](https://img-blog.csdnimg.cn/14ef8d7f9286496b9ad41f25fa17d4e7.png)
鼠标放在box上
鼠标撤回会恢复原状
![](https://img-blog.csdnimg.cn/2337ca6b74d0417d9d31b52ee0988bd7.png)
点击输入框
鼠标点空白处会恢复原状
![](https://img-blog.csdnimg.cn/36b687a2ae0e4109aec1711f9cebad35.png)
点击单选框
再次点击会恢复原状
![](https://img-blog.csdnimg.cn/a0ef969def4843e9805f285710d81ece.png)



