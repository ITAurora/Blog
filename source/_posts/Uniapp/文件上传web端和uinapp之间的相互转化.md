---
title: 文件上传web端和uinapp之间的相互转化
date: 2023-01-11 10:10:10
tags:
  - uni-app
categories:
  - uni-app
index_img: ../tnt/17.jpg
banner_img: ../tnt/17.jpg
excerpt: 摘要
---

## web端

web端文件上传最原始的方法，就是创建FormData对象，在创建的对象里添加属性以及要上传的文件，可以直接使用axios进行上传，上传到后端的minio集群里（个例）。

```js
          let fileData = new FormData();
          fileData.append('file', file);
          fileData.append('path', '/private/' + msgId + '/' + timestamp);
          axios.post(url, fileData).then(res => {
          //上传成功后你要执行的操作
          }).catch(function (error) {
          //上传失败进行的操作
          //比如你所上传的minio集群所分配的存储空间满了
          });
```

## uni-app
我们知道，uniapp和vue很像，像但又不完全像，再uniapp里官方提供的有单独上传文件的api，uni.uploadFile用来上传uniapp的各种文件，不过也能使用axios，想使用axios的话需要基于uni.request再进行封装。

```js
uni.uploadFile({
				url:url,
				file:file, // filePathfile和filefilePath二选一，file放文件流，filefilePath放文件路径
				// name:file.name, // 在FormData 中文件对应的属性名，这个如果你要加path，就不要添加name字段了
				formData: {
					path:'/group/' + msgId + '/' + timestamp//用来添加除上述字段以外的字段
				},
				header: {
					token:token
				},
			  		success: (uploadFileRes) => {
			  		//上传成功后的回调
			  		}
			  		fail:(err)=>{
			  		//上传失败执行的操作
			  		}
			  		});
```
