---
title: ElementUI_cascader value 相同
date: 2019-11-21 16:04:54
tags: ELementUI_cascader value 相同
categories: "ElementUI"
---
# elementUI cascader 不同类别的children value相同
1. 例子 当周和月的value值相同时，当选择月的时候页面显示的是周，但是后台传的值是月。
> 解决方法:周用其他的表示形式 （例：周一 value: monday)
> 如果后台需要的是 周一：1 ，此时自我进行转换
```
options: [{ //options为cascader的值
    value: "everyDay",
    label: "每天"
}, {
    value: "everyWeek",
    label: "每周",
    children: [{
        value: "1",
        label: "星期一"
    }, {
        value: "2",
        label: "星期二"
    }, {
        value: "3",
        label: "星期三"
    }, {
        value: "4",
        label: "星期四"
    }, ..... ]
}, {
    value: "everyMonth",
    label: "每月",
    children: [{
        value: "1",
        label: "一号"
    }, {
        value: "2",
        label: "二号"
    }, {
        value: "3",
        label: "三号"
    }, {
        value: "4",
        label: "四号"
    }, ..... ]
}]
```