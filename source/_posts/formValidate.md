---
title: 表单验证规则联动
date: 2020-01-17 16:31:42
tags: 表单验证规则联动
categories: 
- ElementUI
---
# ElementUI form 表单规则联动

```
<el-form-item label="活动区域" prop="region">
    <el-select v-model="registData.region.country" placeholder="请选择国家">
        <el-option label="国家一" value="USA"></el-option>
        <el-option label="国家二" value="China"></el-option>
    </el-select>
    <el-select v-model="registData.region.city" placeholder="请选择城市">
        <el-option label="城市一" value="shanghai"></el-option>
        <el-option label="城市二" value="beijing"></el-option>
    </el-select>
</el-form-item>

<!--规则写法-->
 region: [
          {
            type: 'object',
            required: true,
            trigger: 'change',
            fields: {
              country: {required: true, message: '请选择国家', trigger: 'blur'},
              city: {required: true, message: '请选择城市', trigger: 'blur'}
            }
          }
        ],
```
