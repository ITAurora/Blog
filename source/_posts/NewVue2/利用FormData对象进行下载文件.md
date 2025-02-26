---
title: 利用FormData对象进行下载文件
date: 2025-02-26 10:10:10
tags:
  - JS
categories:
  - Vue2问题
index_img: ../tnt/6.jpg
banner_img: ../tnt/6.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```js
      const formData = new FormData();
      formData.append('参数1', 参数1);
      formData.append('参数2', 参数2);
      formData.append('参数3', 参数3);
      formData.append('参数4', 参数4);
      formData.append('参数5', 参数5);
      //...............以此类推
      fetch(`/api${PREFIX_URL}/export`, {
        method: 'POST',
        body: formData,
        headers:{
          'token':store.state.token,
          //headers携带的各种数据
        }
      })
        .then(response => {
          if (!response.ok) {
            throw new Error('Network response was not ok');
          }
          return response.blob(); // 将响应转换为 Blob 对象
        })
        .then(blob => {
          // 创建一个链接元素
          const url = window.URL.createObjectURL(blob);
          const a = document.createElement('a');
          a.href = url;
          a.download = this.projectInfo.projectName+'.'+(this.exportInfo.fileType==='1'?'xlsx':'csv'); // 设置下载的文件名
          document.body.appendChild(a);
          a.click(); // 触发下载
          a.remove(); // 移除链接元素
          window.URL.revokeObjectURL(url); // 释放 URL 对象
        })
        .catch(error => {
          console.error('There was a problem with the fetch operation:', error);
        });
```
