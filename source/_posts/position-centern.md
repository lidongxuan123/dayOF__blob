---
title: 使用定位的方式让元素剧中
date: 2020-03-20 09:36:56
tags:  使用定位的方式让元素剧中
categories: web前端css
---

# 1.使用定位的方式让元素居中

<span style="color:red; font-size:16px;">transform: translate(-50%, -50%);</span>

```
.pag1 {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    font-size: 14px;
    color: green;
}
```

# 2. 使用display:flex 实现元素上下左右居中
```
.flex-container {
    display: -webkit-flex;
    /*display: flex;*/
    width: 400px;
    height: 250px;
    background-color: lightgrey;
}

.flex-item {
    background-color: cornflowerblue;
    width: 75px;
    height: 75px;
    margin: auto;
}
<div class="flex-container">
  <div class="flex-item">Perfect centering!</div>
</div>
```