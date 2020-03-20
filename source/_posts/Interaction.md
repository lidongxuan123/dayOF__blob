---
title: 前端的交互方式
date: 2019-11-21 16:40:58
tags: 前端的交互方式 （发送请求）
categories: 
- JavaScript
---

# 前端请求
1. 原生的XMLHttpRequest
> 创建一个XMLHttpRequest对象
xmlhttp = new XMLHttpRequest()
> 设置请求参数
xmlhttp.open("get",url.true)
> 发送请求
xmlhttp.send(null)
> 接受后端返回的值
xmlDoc = xmlhttp.responseText
接受后端的返回值通常会这样做
xmlhttp.onreadystatechange = function() {
    if (xmlhttp.readyState == 4) {
        if(xmlhttp.status == 200) {
            xmlDoc = xmlhttp.responseText
        }
    }
}

# jquery的请求方式
```
$.ajax({
    type: "post",
    contentType: "application/json",
    url: "",
    data: data,      //发送的数据
    success: function(result) {
        <!--请求成功-->
    }
})
```


