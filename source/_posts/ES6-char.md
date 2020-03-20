---
title: ES6-char
date: 2020-01-17 14:54:06
tags: ES6 字符串的扩展
categories: 
- ES6语法
--- 
# ES6字符串扩展
1. 字符串遍历函数
``` 
    for (let i of list) {
        console.log(i)
    }
```
2. includes(), startsWith(), endsWith()
3. 模板字符串
```
    There are <b>${basket.count}</b> items
    in your basket, <em>${basket.onSale}</em>
    are on sale!

    <!--vue项目中-->
    <div :style="width: `${value}px`"></div>
```
