---
title: 使用provide和inject时初始化有效但监不听到provide导出的值的变化
date: 2023-05-25 10:10:10
tags:
  - Js
categories:
  - Vue3问题
index_img: ../tnt/20.jpg
banner_img: ../tnt/20.jpg
excerpt: 摘要
---

这个问题是我自身的沙雕问题，仅供参考。
vue2里肯定不会遇到我这种问题，因为他对data数据源全部进行了响应式绑定
但vue3里的响应式绑定要自己用shallowReactive和reactive进行手动绑定
导致我们有时候会传shallowReactive和reactive内部的值
此时provide和inject是监听不到你的值的（太悲惨了）
错误示例：

```js
// A.vue
setup() {
 const info = reactive({
    name: 'Tony',
    age: 99
  })
  provide('name', info.name) // 导出
 }
// C.vue
setup() {
  const info = inject('name') // 导入
}
```
正确示例
```js
// A.vue
setup() {
 const info = reactive({
    name: 'Tony',
    age: 99
  })
  provide('userInfo', info) // 导出
 }
// C.vue
setup() {
  const info = inject('userInfo') // 导入
  const name=userInfo.name
}
对 你没看错 想要拿name就要把他的shallowReactive和reactive包裹的最外层进行导出
因为这样才有响应式
```
