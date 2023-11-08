---
title: 关于在vue中使用eventBus接收监听被多次触发的解决办法
date: 2021-11-3 10:10:10
tags:
  - JS
categories:
  - Vue2问题
index_img: ../tnt/4.jpg
banner_img: ../tnt/4.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

先看这个bug
创建一个eventBus：
```js
import Vue from "vue";
export default new Vue;
```
兄弟组件分别导入eventBus：

```js
import eventBus from "eventBus";
```
传值：
这里我把传值直接放在了列表更新函数里面进行触发了

```js
fetchList () {
      userList(this.listQuery).then((res) => {
        this.tableData = res.data.data;
        eventBus.$emit('sendByBus', res.data.data)
        this.pageQuery.p = res.data.page
      });
    },
```
接收值：
同时更新界面数据
```js
eventBus.$on("sendByBus", (data) => {
      this.person = data;
      data.map((item, index) => {
        this.allmodelType.push(item.id)
      })
      this.fetchList()
    });
```
问题来了：
当刷新完界面第一次点击tabs
![](../Vue2Img/image.png)
这还挺正常（它本身走一次smList，兄弟走一次userList然后又触发一次smList）
当我点击切换组件的时候 离谱的来了
第二次点击：
![](../Vue2Img/image-1.png)
第三次点击：
![](../Vue2Img/image-2.png)
它会一直累加进行请求 除非你再次刷新界面 它才会从新从1开始再累加 这肯定不行的
为什么会有这个问题呢？？？
首先事件总线是全局的 也就是说 当你每次emit触发一次这条线就已经创建存在了 当整个程序在运行时他就会一直存在 每当你触发一次就会新建一条事件总线 也是为什么会触发多次函数的问题所在
如何解决？？？
既然能创建肯定就能销毁，每次使用后把他销毁不久完了 就像计时器每次使用完都会有其相应的clear
组件销毁前销毁当前事件总线：
```js
beforeDestroy(){
    eventBus.$off("sendByBus",)
  },
```
