---
title: cssFloat 两种简单的清理浮动的方法
date: 2019-11-14 10:59:44
tags: 两种简单的清理浮动的方法
categories:
- web前端css
---

# 清理浮动
1. 在使用浮动元素的最后面清理浮动
```
<div>
    <div style="float:left"></div> (向左浮动)
    <div style="float:left"></div> (向左浮动)
    <div style="clear:both"></div>
</div>
```
2. 在父元素后面清理浮动
```
<div class="out">
    <div style="float:left"></div> (向左浮动)
    <div style="float:left"></div> (向左浮动)
</div>
<style>
    .out:after {
        content:"",
        display:block;
        clear:both
    }
</style>

```