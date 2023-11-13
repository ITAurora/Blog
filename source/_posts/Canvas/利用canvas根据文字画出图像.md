---
title: 利用canvas根据文字画出图像
date: 2021-12-16 10:10:10
tags:
  - Canvas
categories:
  - Canvas
index_img: ../tnt/6.jpg
banner_img: ../tnt/6.jpg
excerpt: 摘要
---

<meta name="referrer" content="no-referrer"/>

```js
getImg(size, text,color) {
	let colors = [
	"#fd8a23", '#128ad2',
	];
	let cvs = document.createElement("canvas");
	cvs.setAttribute('width', size[0]);
	cvs.setAttribute('height', size[1]);
	let ctx = cvs.getContext("2d");
	ctx.fillStyle = colors[color];
	ctx.fillRect(0, 0, size[0], size[1]);
	ctx.fillStyle = 'rgb(255,255,255)';
	ctx.font = size[0]*0.6+"px Arial";
	ctx.textBaseline = "middle";
	ctx.textAlign = "center";
	ctx.fillText(text,size[0]/2,size[1]/2);
	return cvs.toDataURL('image/jpeg', 1);
	}
```
