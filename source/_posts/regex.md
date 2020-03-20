---
title: 正则去除换行和空格
date: 2020-01-17 15:59:27
tags: 正则表达式去除换行和空格
categories: 
- JavaScript
---
# 正则表达式去除所有的空格
1. 去除所有空格
str.replace(/\s/g,"")
2. 去除所有非数字字符
str.replace(/[^a-zA-Z0-9]/g,"")
3. 去除换行
str.replace(/[\r\n]/g/, "")
4. 是否是数字组成
let str = "********"
reg = /^[0-9]*$/
reg.test(str)