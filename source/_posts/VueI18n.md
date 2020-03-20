---
title: vue 国际化
date: 2019-11-15 11:06:57
tags: vue 国际化
categories: Vue项目知识
---

# 国际化
1. 安装 vue-i18n
```
    npm install vue-i18n
```
2. 导入文件main.js中
```
import VueI18n from 'vue-i18n'
Vue.use(VueI18n)
const i18n = new VueI18n({
    locale: 'zh-CN',    // 语言标识
    //this.$i18n.locale // 通过切换locale的值来实现语言切换
    messages: {
        'zh-CN': require('./common/lang/zh'),   // 中文语言包
        'en-US': require('./common/lang/en')    // 英文语言包
    }
})
    new Vue({
    el: '#app',
    i18n,  // 不要忘记
    store,
    router,
    template: '<App/>',
    components: { App }
    })
```
