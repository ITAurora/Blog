---
title: ajax的post请求数据为json格式相关设置
date: 2023-02-09 10:10:10
tags:
  - ajax
categories:
  - JS问题
index_img: ../tnt/8.jpg
banner_img: ../tnt/18.jpg
excerpt: 摘要
---

平时用request封装axios习惯了突然用ajax传参时一直出问题，原来是配置设置错了

```js
$.ajax({
        type: "post",
        contentType: "application/json",//必须项
        dataType: "json",//必须项
        data: JSON.stringify({
            data: "world",
            p: {
                pag: 0,
                pageSize: 0,
                total: 0
            },
            token: "string"
        }),
        // async: true,
        url: " http://61.155.137.231:9006/beClass/classList",
        success: function (res) {
            console.log(res);
        },
        error: function (err) {
            console.log("请求失败", err.statusText);
        }
    });
```
