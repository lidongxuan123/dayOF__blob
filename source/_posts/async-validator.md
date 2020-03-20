---
title: element UI 表单的自定义规则
date: 2020-03-02 11:24:42
tags: element UI 表单的自定义规则
categories: 
- ElementUI
---

# 如何批量的给表单设置自定义规则
> 1.示例：
```
使用element ui的规则定义方式，把规则定义为全局函数
var checkAge = (rule, value, callback) => {
  console.log(rule)
  console.log(value)
        if (!value) {
          return callback(new Error('年龄不能为空'));
        }
        if(value) {
          if(value < rule.testvalue) {
            return callback(new Error('年龄不能小于'+ rule.testvalue));
          } else {
            return ;
          }
        }
      };

function lic (Vue) {
  Vue.prototype.checkAge = checkAge
}

export default lic

```
> 2.项目中使用方式
```
 rule: {
    age:{ validator: this.checkAge, trigger: 'change', testvalue: 22 }
    }
```

> 3.在main.js里引入
``` 
    import lic from "./rule/index.js"
    lic(Vue)
```
