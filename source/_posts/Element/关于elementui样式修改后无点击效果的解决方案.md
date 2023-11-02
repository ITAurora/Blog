---
title: 关于elementui样式修改后无点击效果的解决方案
date: 2021-9-3 10:10:10
tags:
  - Element-Ui
categories:
  - Element
index_img: ../tnt/1.jpg
banner_img: ../tnt/1.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

使用栅格布局后（其他方式也会无效）下拉和checkbox都无反应
解决办法：在最外层套个盒子 给个overflow: hidden属性
```html
<div style="overflow: hidden">
          <el-col :span="12">
            <el-form-item label="分组名称1" prop="region">
              <el-select
                v-model="ruleForm.region"
                :placeholder="tableData[0].lxmc"
                style="width: 80%"
              ><div  v-for="(item, i) in tableData"
            :key="item.lxmc+i">
                <el-option :label="item.lxmc" :value="item.lxmc"></el-option>
                </div>
              </el-select>
            </el-form-item>
            <el-form-item label="分组名称2" prop="name">
              <el-input
                v-model="ruleForm.name"
                style="width: 80%"
                placeholder="请输入"
              ></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="12">
            <el-form-item label="活动区域" prop="region">
              <el-select
                v-model="ruleForm.region"
                placeholder="请选择活动区域"
                style="width: 80%"
              >
                <el-option label="区域一" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="特殊资源" prop="resource">
              <el-radio-group v-model="ruleForm.resource">
                <el-radio label="本地" style="margin-right: 10px"></el-radio>
                <el-radio label="全国" style="margin-right: 10px"></el-radio>
                <el-tag
                  type="info"
                  style="background-color: white; border: none"
                  >(单选)</el-tag
                >
              </el-radio-group>
            </el-form-item>
          </el-col>
        </div>
```
关于下拉遍历后出现多个下拉框和一个选项
解决方案：外层套盒子 在盒子上进行遍历 就会展示为一个下拉框展示多个选项
添加盒子前：

```html
<el-form-item label="活动区域" prop="region">
              <el-select
                v-model="ruleForm.region"
                placeholder="请选择活动区域"
                style="width: 80%"
               v-for="(item, i) in tableData"
            :key="item.lxmc+i"
              ><div>
                <el-option label="区域一" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
                </div>
              </el-select>
            </el-form-item>
```

添加盒子后
```html
<el-form-item label="分组名称" prop="region">
              <el-select
                v-model="ruleForm.region"
                :placeholder="tableData[0].lxmc"
                style="width: 80%"
              ><div  v-for="(item, i) in tableData"
            :key="item.lxmc+i">
                <el-option :label="item.lxmc" :value="item.lxmc"></el-option>
                </div>
              </el-select>
            </el-form-item>
```

或者直接遍历本标签

```html
<el-option  v-for="(item, i) in tableData"
            :key="item.lxmc+i" :label="item.lxmc" :value="item.lxmc"></el-option>
```
