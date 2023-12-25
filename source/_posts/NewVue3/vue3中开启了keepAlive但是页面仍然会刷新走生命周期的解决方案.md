---
title: vue3中开启了keepAlive但是页面仍然会刷新走生命周期的解决方案
date: 2023-10-10 10:10:10
tags:
  - Js
categories:
  - Vue3问题
index_img: ../tnt/30.jpg
banner_img: ../tnt/30.jpg
excerpt: 摘要
---

我们知道vue3里我们不需要写name和components等等,脚手架会以文件名为组件名来让我们导入并使用,然后我遇到一个很小的问题,就是我开启了keepAlive 如下:

```javascript
 {
    path: "styleProcess",
    name: "styleProcess",
    component: resolve => import("@/views"),
    meta: {
        keepAlive: true
    }
  }
```
但是呢我在这个页面操作后像select的选中,抽屉的打开 ,dialog的打开等操作后,进入其他页面后再返回到刚才操作的页面,上面哪些举例都会重置,不会保留之前的操作.正常情况下开启了keepAlive是会保存的vue2是没问题的,vue3会遇到这个问题,这个时候我们就需要加name字段了,如下:

```javascript
<script>
export default {
  name: "",
};
</script>
```
就可以完成页面缓存了
