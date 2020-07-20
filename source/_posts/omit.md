---
title: omit / loadsh(对象操作)
date: 2020-06-29 16:35:07
tags: omit 去除对象中的某些项
categories: 
- npm包知识
---

#omit
>>>调用格式：_.omit(object, *keys)  该函数的功能是：返回一个没有列入排除key属性的对象。其中，参数object为JSON格式的对象，*keys表示多个需要排除掉的key属性。示例如下
```
const _ = require('lodash/object');
const originObject = {
  A: 1,
  B: 2,
  C: 3,
  D: 4
};
const newObject = _.omit(originObject, 'B', 'C');
{ A: 1, D: 4 }
```






# loadsh
> pick
```
const _ = require('lodash/object');
const originObject = {
  A: 1,
  B: 2,
  C: 3,
  D: 4
};
const newObject = _.pick(originObject, 'B', 'C');
```
{ B: 2, C: 3 }

const _ = require('lodash');


> pickBy
```
const originObject = {
  A: 1,
  B: 2,
  C: 3,
  D: 4,
  E: '5',
  F: true
};
const newObject = _.pickBy(originObject, _.isString);
{ E: '5' }
```
app.get("/api/user",function(req,res,next){
    createProxyMiddleware({ target:'http://www.example.org', 
    changeOrigin: true }
    res.send("111")
})
app.get("/api/user",createProxyMiddleware({                   target:'http://www.example.org', 
    changeOrigin: true })



