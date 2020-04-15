---
title: 下拉框是tree
date: 2020-03-31 17:21:41
tags: select下拉框是树
categories: 
- ElementUI
---

# 基于下拉框的树
```
<template>
  <div>
    <el-select v-model="value" multiple filterable allow-create collapse-tags placeholder="请选择文章标签">
      <el-option value="" style="height:auto;padding:0">
        <!--@check-change="check_right_change"-->
        <el-tree ref="tree" :data="data" show-checkbox node-key="id" :props="defaultProps" @check-change="getnodes">
        </el-tree>
      </el-option>
    </el-select>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        value:[],
        data: [{
          id: 1,
          label: '一级 1',
          children: [{
            id: 4,
            label: '二级 1-1',
            children: [{
              id: 9,
              label: '三级 1-1-1'
            }, {
              id: 10,
              label: '三级 1-1-2'
            }]
          }]
        }, {
          id: 2,
          label: '一级 2',
          children: [{
            id: 5,
            label: '二级 2-1'
          }, {
            id: 6,
            label: '二级 2-2'
          }]
        }, {
          id: 3,
          label: '一级 3',
          children: [{
            id: 7,
            label: '二级 3-1'
          }, {
            id: 8,
            label: '二级 3-2'
          }]
        }], 
        defaultProps: {
          children: 'children',
          label: 'label'
        }
      }
    },
    methods: {
      getnodes(val) {
        let self = this
        self.value = []
       console.log(this.$refs.tree.getCheckedNodes(true, true))
       let listNodes = this.$refs.tree.getCheckedNodes(true, true)
       listNodes.forEach(function(element) {
         let obj = {
           id: element.id,
           label: element.label
         }
         self.value.push(element.label)
       });
      }
    }
  }

</script>
```