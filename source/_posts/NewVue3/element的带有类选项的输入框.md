---
title: 带有类选项的输入框
date: 2023-06-08 11:10:10
tags:
  - Js
categories:
  - Vue3问题
index_img: ../tnt/22.jpg
banner_img: ../tnt/22.jpg
excerpt: 摘要
---

组件代码

```vue
<!-- 搜索栏  -->
<template>
    <div class='SearchBar'>
        <div class="SearchBox">
            <template v-for="(item, index) in list" :key="index+'switchBox'">
                <div @click="change($event, item, index)" class="SearchBoxOptions"
                    :class="{ 'SearchBoxOptionsChance': activeValue == item.value }">
                    {{ item.label }}</div>
            </template>
        </div>
        <div class="SearchContent">
            <div class="Searchinfo">
                <div class="icon">
                    <el-icon>
                        <Search />
                    </el-icon>
                </div>
                <input ref="input" type="text" id="searchContent" name="name" required size="40" placeholder="请输入搜索内容" @click="inputClick">
                <div class="icon">
                    <el-icon>
                        <Camera />
                    </el-icon>
                </div>
                <div class="iconOption" @click="search">
                    <el-icon>
                        <Search />
                    </el-icon>
                </div>
            </div>
        </div>
    </div>
</template>
<script setup lang='ts'>
import { reactive, shallowReactive, watch, ref, onBeforeMount, onMounted, nextTick, defineProps, defineEmits } from 'vue'
import { Search } from '@element-plus/icons-vue'
import { useRoute, useRouter } from 'vue-router';
import { ElMessage, useFormItemInputId } from 'element-plus';
import kaloneUtils from '@/utils/kaloneUtils';
const route = useRoute();
const router = useRouter();
const props = defineProps({
    activeValue: {
        type: [String, Number],
        default() { return '' }
    },
    searchValue: {
        type: String,
        default() { return '' }
    }

})
const emits = defineEmits(['update:activeValue', 'tabsChange', 'update:searchValue', 'searchTab',])
const input = ref(null)
const list = [{ label: '商品', value: 'shop' }, { label: '供应商', value: 'supplier' }]
const inputClick=()=>{
    // console.log('input被点击了')
}
const change = (event: any, item: any, index: any) => {
    emits('update:activeValue', item.value)
    emits('tabsChange', event, item, index)
}
const search = () => {
    emits('update:searchValue', input.value.value)
    emits('searchTab', input.value.value)
}
onMounted(() => {
    input.value.value = props.searchValue
})
</script>
<style scoped lang='less'>
.SearchBar {
    width: 530px;
    margin: 0 auto;

    .SearchBox {
        display: flex;
        justify-content: left;
        align-items: center;
        width: 100px;

        .SearchBoxOptions {
            width: 50%;
            cursor: pointer;
            text-align: center;
            height: 30px;
            line-height: 30px;
        }

        .SearchBoxOptionsChance {
            background: linear-gradient(135deg, #FF4D6D, #F29984);
            color: #ffffff;
        }
    }

    .SearchContent {
        .Searchinfo {
            width: 100%;
            border: 1px solid red;
            border-right: none;
            height: 50px;
            display: flex;
            justify-content: left;
            align-items: center;

            .icon {
                width: 50px;
                height: 50px;
                cursor: pointer;
                line-height: 50px;
                text-align: center;
                font-size: 15px;
                color: gray;
            }

            .icon:hover {
                color: red;
            }

            .iconOption {
                flex: 1;
                background: linear-gradient(135deg, #FF4D6D, #F29984);
                height: 50px;
                line-height: 50px;
                text-align: center;
                color: white;
                font-size: 25px;
                cursor: pointer;
            }
        }
    }
}
</style>
```
组件使用

```vue
  <SearchBar
   v-model:activeValue="type"
   v-model:searchValue="keyWords"
     @tabsChange="tabsChange"
      @searchTab="searchOption">
   </SearchBar>
```
