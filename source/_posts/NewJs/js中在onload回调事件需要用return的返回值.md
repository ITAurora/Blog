---
title: js中在onload回调事件需要用return的返回值
date: 2022-12-13 10:10:10
tags:
  - JS
categories:
  - JS问题
index_img: ../tnt/16.jpg
banner_img: ../tnt/16.jpg
excerpt: 摘要
---

按照平常理论上这样写一点问题也没问题
但是返回的是undefined
说明onload要等待x资源都加再完成了才能执行
```js
getFileSize(url) {
      var x = new XMLHttpRequest();
       x.open("GET", url, true);
       x.responseType = 'blob';
       var fileSize=0
       x.onload = () => {
      console.log(x.response.size)
      fileSize=x.response.size
      }
      x.send();
      return fileSize
}
```
改进 利用promise的回调
```js
getFileSize(url) {
      return new Promise(function (a, b) {
        var x = new XMLHttpRequest();
        x.open("GET", url, true);
        x.responseType = 'blob';
        x.onload = () => {
          console.log(x.response.size)
          a(x)
        }
        x.send();
      })
    }
```
后续所有操作都在这回调里面执行
```js
getFileSize(url).then((res)=>{
“你要操作”
})
```