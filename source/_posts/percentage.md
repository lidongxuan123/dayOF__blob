---
title: 解决element ui 进度条组件percentage超出100
date: 2020-03-03 14:36:24
tags: 解决element ui 进度条组件percentage超出100
categories: 
- ElementUI
---

# 解决elememt ui 组件percentage超出100

```
<el-progress :percentage="value > 100 ? 100 : value" :format="_format(value)"></el-progress>
```
由于format处理的只是进度条文本的展示效果, 而且该参数只接收一个函数, 所以可以通过以下方式保持超过100仍按100显示, 但文本可以显示实际值:

```
_format(value) {
    return () => {
      return value + '%'
    }
}
```