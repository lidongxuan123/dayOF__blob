---
title: Vue.nextTick(函数的解释和使用)
date: 2019-11-21 16:20:42
tags: Vue.nextTick(函数的解释和使用)
categories: 
- Vue项目知识
---

# Vue.nextTick(函数的解释和使用)
1. 解释
>  在下次 DOM 更新循环结束之后执行延迟回调。在修改数据之后立即使用这个方法，获取更新后的 DOM。nextTick()，是将回调函数延迟在下一次dom更新数据后调用，简单的理解是：当数据更新了，在dom中渲染后，自动执行该函数。
2. 使用
    ```
    this.$nextTick(() => {
      //执行的函数主题
    })
    ```
3. 例子
> 目前没有找到相应的例子，后续补充
<font color="#FF0000">目前没有找到相应的例子，后续补充</font>
