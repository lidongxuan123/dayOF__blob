---
title: compression 返回值进行压缩
date: 2020-06-29 11:25:58
tags: compression 返回值进行压缩
categories: 
- npm包知识
---
# compression 返回值进行压缩
```
var compression = require('compression')

```
# 使用方式

```
app.use(compression({
    chunkSize: "大小" 默认 zlib.Z_DEFAULT_CHUNK 或者 16384  zlib来自 var zlib = require("zlib),
    filter: function(req,res) {

    },
    level: 压缩级别，级别越高,压缩效果越好,但时间越长  属性值是integer类型 范围是0-9,  0为不压缩'-1'  为特殊值, 相当于取默认压缩值,(取效果和性能的折中,大概6级左右)，
    memLevel: 内存分配级别：integer类型,范围1-9,  默认是8级
    strategy: 优化压缩算法

}))

```
