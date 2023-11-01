---
title: vue基础
date: 2021-3-4 10:10:10
tags:
  - Vue2
categories:
  - Vue2
index_img: ../articleImages/17.jpg
banner_img: ../articleImages/17.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

**vue的声明式渲染**
html```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>vue基础之声明式渲染</title>
</head>
<body>
<div id="app">
    {{ message }}
</div>
</body>
</html>
<!--cdn引入，后面会有脚手架。所谓cdn就是引用别人的代码比如说别人服务器里的代码 而脚手架是直接在本机的就不需要cdn引入看-->
<script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
<script>
    var app = new Vue({
        el: '#app',//将一个 Vue 应用挂载到一个id为app的DOM元素上，后续所有的操作将都会在Vue实例内部完成。
        data: {
            message: 'Hello Vue!'
        }//数据和DOM被建立了关联，所有东西都是响应式的。现在只有一条数据，以后会有很多很多dom节点和数据会一一关联并互相响应。
    })
</script>
```
**vue基础介绍**

html```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>vue基础介绍</title>
</head>
<body>
<div id="one">
    <!--除了调用vue应用数据源的data外还可以绑定元素attribute（属性）这些都是vue写好暴露出来让我们直接用的-->
    <span v-bind:title="message"><!--这里v-bind attribute 被称为指令 调用其attribute的语法-->
    <!-- v-bind:title="message"的意思就是将这个元素节点的 title attribute 和 Vue 实例的 message property 保持一致-->
    鼠标悬停几秒钟查看此处动态绑定的提示信息！
    </span>
    <!--条件与循环-->
    <div id="app-3">
        <p v-if="seen">你能看到这个</p><!--利用数据源里seen值的真假true，false控制这个p标签是否出现在界面上-->
        <p v-if="!seen">你看不到这个</p><!-- v-if和v-show有相同的共功能 本质区别一个是删除dom一个是display为none-->
        <!--当我们要根据数据生成多个dom的时候vue为我们提供了v-for这个方法-->
        <ol>
            <li v-for="todo in todos">
                {{ todo.text }}
            </li>
        </ol>
        <!--界面肯定要与用户交互的，vue为我们提供了v-on指令来监听用户的操作，通过它调用在 Vue 实例中定义的方法-->
        <!--vue实例中data是数据源，那么methods就是方法源（存放各种行为的地方）-->
        <button v-on:click="reverseMessage">反转消息</button>
        <p>{{ message }}</p>
        <!--当我们遇到表单vue为我们提供了v-model方法来达到数据和界面同步的效果-->
        <input v-model="message">
        <!--创建一个todo-item组件的实例 -->
        <todo-item1></todo-item1>
        <todo-item2
                v-for="item in todos"
                v-bind:todo="item"
                v-bind:key="item.id"
        ></todo-item2>
    </div>
</div>
</body>
</html>
<script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
<script>
    // 定义名为todo-item的新组件
    Vue.component('todo-item1', {
        template: '<li>这是一个组件</li>'//这是直接写在了注册组件里面代码，后续会分离出成一个文件，在此只注册组件名，之后直接可以在页面使用此组件
    })
    Vue.component('todo-item2', {
        //组件todo-item组件现在接受一个"prop"，类似于一个自定义 attribute。这个prop名为todo来自他的父亲。
        props: ['todo'],
        template: '<li>{{ todo.text }}</li>'
    })
    var vue=new Vue({
        el:'#one',
        data:{
            message: '页面加载于 ' + new Date().toLocaleString(),
            seen:true,
            todos: [
                { text: '学习 JavaScript' },
                { text: '学习 Vue' },
                { text: '整个牛项目' }
            ],
        },
        methods: {
            reverseMessage: function () {
                this.message = this.message.split('').reverse().join('')
                //这就体现了vue的好处，我们只修改了message的值，但没有触碰绑定了message的DOM，因为vue代替我们进行了操作dom，我们只需要关注自己写代码的逻辑
            }
        }
    })
</script>
```
