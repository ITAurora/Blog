---
title: vue2中使用vuex全面解析
date: 2023-09-01 10:10:10
tags:
  - Vue2
categories:
  - Vue2
index_img: ../tnt/29.jpg
banner_img: ../tnt/29.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

# vue2中使用vuex全面解析
初入前端写的是vue2，近些年一直在做vue3的项目，久未接触过vue2的代码了，今日突然维护了一个v2项目记忆已不似当年，今日对我以往所有接触的vuex使用做个总结。
## vue2中使用vuex基础模板
### store文件夹下的index.js文件
```javascript
import Vue from 'vue'
import Vuex from 'vuex'
import modName from './mod'
Vue.use(Vuex)
export default new Vuex.Store({
	//state用来存放数据,类似data
  state: { 
    name:'蔡徐坤',
    age:'一坤年',
    sex:'男'
  },
   //getters用来返回你基于state想要的新状态,类似于computed(调用时不可以传参数)
   getters:{
    getDescripton(state){
      return state.name+state.age+state.sex
    },
  },
  //mutations用来修改你存放的state数据,类似methods(调用时可以传参数data，注意:这里面只能放同步的方法)
  mutations: {
   getNewName(state,data) {
      state.age++;
      state.name=state.name+data
    }
  },
   //actions也是用来修改你存放的state数据,但是它是通过调用mutations里的方法来实现修改state的值的,actions中的方法默认是异步的,因为他返回的是一个promise对象，由此可见,actions里可以放异步的方法，弥补了mutations不能放异步方法的缺点
  actions: {
 //context上下文可以理解为它是当前的this
  async getUserInfo(context,url){ 
  const res = await axios.get(url)
  //相当于 this.$store.commit,第一个参数是方法名，第二个参数是要传入的数据data
  context.commit('getNewName',res) 
    },
  },
  //分模块的情况下要用到
  modules: {
  mod
  }
})
```
### mod.js文件
```javascript
export default{
 namespaced: true,//namespaced: true 的方式使其成为带命名空间的模块。保证在变量名一样的时候，添加一个父级名拼接
  state:{
  modName:'mod蔡徐坤';
    },
  mutations: {
   getNewName(state,data) {
      state.age++;
      state.name=state.name+data
    }
  },
   actions: {
  async getUserInfo(context,url){ 
  const res = await axios.get(url)
  context.commit('getNewName',res) 
    },
  },
   getters:{
    getDescripton(state){
      return state.name+state.age+state.sex
    },
}
```
### 页面使用
取state值
```javascript
//直接使用
this.$store.state.name//非模块
this.$store.state.mod.modName//模块

//辅助函数emapState
computed:{
//取非模块里值时
...mapState(['name'])//默认name取vuex的name值
...mapState({newName:'name'})//newName取vuex的name值(重命名)
...mapState({newName: state => state.name,})//函数取法更灵活
//取mod模块里的值时
 ...mapState('mod', ['modName']), 
 ...mapState('mod', {'newModName': 'modName'})
 ...mapState({newModName: state => state.newModName.modName,})//函数取法更灵活
}

```

取getter值

```javascript
//直接使用
this.$store.getters.getDescripton//非模块
this.$store.getters.mod.getDescripton//模块

//辅助函数mapGetters
computed:{
//取非模块里值时
...mapGetters(['getDescripton'])
...mapGetters({mewGetDescripton:'getDescripton'})
//取mod模块里的值时
...mapGetters('mod',['getDescripton'])
...mapGetters('mod',{mewGetDescripton:'getDescripton'})
}
```
mutations修改值

```javascript
//直接使用
this.$store.commit('getNewName', data)//非模块
this.$store.commit('mod/getNewName', data)//模块

//辅助函数mapMutations
methods: { 
  //取非模块里值时
  ...mapMutations(['getNewName']), 
  ...mapMutations({'NewGetNewName': 'getNewName'})
  //取mod模块里的值时
  ...mapMutations('mod', ['getNewName']), 
  ...mapMutations('mod',{'NewGetNewName': 'getNewName'})
}
```

actions修改值
```javascript
//直接使用
this.$store.dispatch('getUserInfo', url)
this.$store.dispatch('mod/getUserInfo', getUserInfo)
//辅助函数mapActions
methods: { 
  ...mapActions(['getUserInfo']), 
  ...mapActions({'newGetUserInfo': 'getUserInfo'})
  ...mapActions('mod', ['getUserInfo']), 
  ...mapActions('mod',{'newGetUserInfo': 'getUserInfo'})
}
```

麻了麻了..........

