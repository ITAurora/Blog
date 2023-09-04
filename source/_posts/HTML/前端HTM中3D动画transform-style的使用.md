---
title: 前端HTM中3D动画transform-style的使用
date: 2020-10-26 10:10:10
tags:
  - HTML
categories:
  - 前端三剑客
index_img: ../articleImages/16.jpg
banner_img: ../articleImages/16.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
		<style type="text/css">
			.root{
				width: 600px;
				height: 600px;
				background-color: pink;
				margin: 30px auto;
				/*开启3D效果 在父标签设置*/
				transform-style: preserve-3d;
				transform:rotateY(30deg) rotateX(30deg);
			}
			.root div{
				width: 300px;
				height: 300px;
				position: absolute;
				top: 0;
				bottom: 0;
				left: 0;
				top: 0;
				margin: auto;
				
			}
			.one{
				background-color: gold;
				animation: move 3s linear infinite;
			}
			@keyframes move{
				0%{
					transform: translateZ(0);
				}
				20%{
					transform: translateZ(100px);
				}
				40%{
					transform: translateZ(0px);
				}
				60%{
					transform: translateZ(-100px);
				}
				80%{
					transform: translateZ(0px);
				}
				100%{
					transform: translateZ(0px);
				}
			}
			.two{
				background-color: green;
			}
		</style>
	</head>
	<body>
		<div class="root">
			<div class="one"></div>
			<div class="two"></div>
		</div>
	</body>
</html>

```
运行结果：
黄色方块在绿色区域上下移动
![](https://img-blog.csdnimg.cn/6d30696199764d91b021c7a98ee71bc5.png)
![](https://img-blog.csdnimg.cn/96f66b71395a48a19b852f3f2282f58f.png)

