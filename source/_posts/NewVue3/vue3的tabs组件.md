---
title: vue3的tabs组件
date: 2023-06-08 10:10:10
tags:
  - Js
categories:
  - Vue3问题
index_img: ../tnt/21.jpg
banner_img: ../tnt/21.jpg
excerpt: 摘要
---

组件代码

```js
<!--  switch切换组件 -->
<template>
    <div class='MoneyNumberSwitch'>
        <template v-for="(item, index) in list" :key="index+'switchBox'">
            <div @click="moneyNumberSwitch(item.value,index)" class="switchBox" :class="{ 'active': indexTab == index }">
                {{ item.label }}</div>
        </template>
        
    </div>
</template>
<script>
import { reactive, shallowReactive, watch, ref, onBeforeMount, onMounted, nextTick, defineProps, defineEmits ,onUpdated} from 'vue'

export default {
    name: 'MoneyNumberSwitch',
    components: {
       
    }
}
</script>
<script setup>
const props = defineProps({
    list:{
        type:Array,
        default(){
            return []
        }
    },
    indexTab:{
        type:[String,Number],
        default:"0"
    }
})
const emits = defineEmits(['update:indexTab','tabsChange'])
const moneyNumberSwitch=(type,index)=>{
    emits('update:indexTab',index)
    emits('moneyNumberSwitch',type,index)
}

</script>
<style scoped lang='less'>
.MoneyNumberSwitch {
    width: 140px;
    height: 25px;
    border-radius: 15px;
    background-color: #D4E4FF;
    justify-content: space-between;
    display: flex;
    border: 1px solid #2779FF;
    .switchBox {
        width: 70px;
        height: 25px;
        text-align: center;
        line-height: 25px;
        font-size: 13px;
        cursor: pointer;
        color: #2779FF;
        transition: all linear .3s;
        border-radius: 15px;
    }

    .active {
        background-color: #2779FF;
        color: #FFFFFF;
    }
}
</style>
```
组件使用

```vue
<MoneyNumberSwitch v-model:indexTab="moneyNumberSwitchData.indexTab" :list="moneyNumberSwitchData.list" @moneyNumberSwitch="moneyNumberSwitch"></MoneyNumberSwitch>
```
