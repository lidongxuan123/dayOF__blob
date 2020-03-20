---
title: 解决margin最上面元素向下margin的时候，父元素也向下margin
date: 2019-11-14 11:08:53
tags: 
- 解决margin最上面元素向下margin的时候，父元素也向下margin
categories: 
- web前端css
---

# 内部元素margin向下，父元素也跟着向下
> 解释：当一个元素包含另一个元素时，假设没有内边距Padding或边框border把外边距分隔开，它们的上下边距会发生合并
![alt 内外元素合并](/images/css/marginQues/marginQuestion_1.png)

> 解决方法:给父元素一个margin / padding 把元素分开