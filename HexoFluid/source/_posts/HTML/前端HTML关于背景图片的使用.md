---
title: 前端HTML关于背景图片的使用
date: 2020-03-11 10:11:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/9.jpg
banner_img: ../articleImages/9.jpg
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
				width: 300px;
				height: 300px;
				border: 20px dashed gold;
				padding: 30px;
				margin: 0 auto;
				/*2.设置背景图片url地址链接*/
				background-image: url(img/1.png);
				/*2.设置图片屏平铺效果
				 图片小于标签尺寸 就会自动平铺充满整个标签
				 repeat-x 仅x轴方向平铺
				 repeat-y 仅y轴方向平铺
				 no-reoeat 不平铺
				 */
				background-repeat: no-repeat;
				/*3.设置背景图片的位置
				 默认left top
				 可以设设置方位词 center right bottom left等
				 可以直接设置px像素值 以及百分比%值
				 */
				background-position: center;
				/*4.background-size 背景图片尺寸
				 a.px数值
				 b.百分比 参考当前标签宽度
				 c.cover 按照比例缩放图片 .cover会让图片充满整个容器
				 有可能造成图片无法显示完整
				 d.contain 按照比例缩放图片. contain按照比例缩放图片
				 只要宽或者高一个方向铺满容器 就立刻停止缩放 有可能造成内容留白
				 
				 */
				background-size: contain ;
				/*5.background-origin
				 完整的第一张图片的开始位置
				 a.border-box 从边框位置开始
				 b.padding-box 从padding位置开始
				 c.content-box 从内容位置开始
				 */
				background-origin: border-box;
				/*6.裁剪 background-clip： 开始裁剪的位置
				 a.border-box 从边框位置之外的部分裁剪
				 b.padding-box 把padding之外的部分裁剪
				 c.content-box 把宽高之外的部分裁剪掉
				 */
				background-clip: content-box;
				/*以上综合写法*/
				/*background: url(img/1.png) no-repeat center content-box;*/
				/*注意 尺寸最好单独设置*/
				/*background-size: conver;*/
			}
			.two{
				background: url(img/1.png) no-repeat center content-box;
				/*注意 尺寸最好单独设置*/
				background-size: contain;
			}
		</style>
	</head>
	<body>
		<div class="one">
			<h1>hi，girl！</h1>
		</div>
		<div class="two">
			<h1>hi，girl！</h1>
		</div>
	</body>
</html>

```

运行结果：
![](https://img-blog.csdnimg.cn/9b26a1eef77547c5a657fd46665d60c1.png)

