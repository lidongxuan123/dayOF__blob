---
title: element-resize-detector
date: 2019-12-23 11:20:03
tags: element-resize-detector 监听元素改变
categories: 
- npm包知识
---

# 安装
> npm install element-resize-detector
# 使用
```
var elementResizeDetectorMaker = require("element-resize-detector");
var erd = elementResizeDetectorMaker();

var erdUltraFast = elementResizeDetectorMaker({
  strategy: "scroll" //<- For ultra performance.
});

```
# API 