---
title: 前端HTML中transform2D变换
date: 2020-10-25 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
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
			.one{
				width: 300px;
				height: 300px;
				background-color: pink;
				/*平移 单位是px
				 translate（30px）x
				 translate（20px，30px）x轴 y轴
				 traslateX(30px) traslate(30px)
				 */
				/*transform: translate(20px,30px);*/
				transition: all .6s linear;
			}
			.one:hover{
				transform: translate(30px,50px);
				opacity: 0.3;
			}
			/*缩放属性测试*/
			.img1{
				width: 600px;
				/*scale缩放比例 没有单位
				 scale(倍数) xy轴方向同时缩放倍数
				 scaleX() scaleY()
				 */
				/*transform: scale(20px);*/
				transition: all .6s linear;
				/*transform: translateX(150px);*/
				/*--------尽量先改中心点 放在hover里会比较丑---------*/
				/*transform-origin: top center;*/
			}
			.img1:hover{
				/*平移属性向右为x轴向下为Y轴*/
				transform: translateX(150px) scale(1.2);
				/*倾斜属性值 skew 单位是deg角度 
				 倾斜属性向右为y轴向下为x轴*/
				/*transform: translateX(150px) skewX(30deg);*/
				/*旋转属性 rotate 向右为x轴向下为Y轴*/
				/*transform: translateX(60px) rotateZ(360deg);*/
				/*旋转的中心点 默认在标签的中心*/
				/*transform-origin: top center;*/
			}
		</style>
	</head>
	<body>
		<!--
			transform 2D变换 注意此属性会使标签发生形变 但不会影响
			盒模型的大小 所以和动画是最佳搭配
			1.translate 平移
			2.scale 缩放
			3.skew 倾斜(不常用)
			4.rotate 旋转
		-->
		<div class="one">测试平移</div>
		<h1>这是一个大标题</h1>
		<div class="img1"><img src="img/1.png"/></div>
		<h1>这是一个大标题</h1>
	</body>
</html>

```
运行结果：
初始界面
![](https://img-blog.csdnimg.cn/e7aed80100f04c518195050fb3a7c55f.png)
鼠标放box上
![](https://img-blog.csdnimg.cn/3a86abf4ed104015b6c7f23735daea53.png)
鼠标放图片上
![](https://img-blog.csdnimg.cn/160538d9a4994d6ea46e233ca1c44fc8.png)



