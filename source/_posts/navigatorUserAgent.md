---
title: Navigator User Agent
date: 2020-03-18 11:10:44
tags: Navigator User Agent
categories:
- JavaScript
---
# 使用方式
> navigator.userAgent

#Navigator对象属性
platform: 返回运行的浏览器的操作系统平台
# 判断系统类型
```
var userAgent =  window.navigator.userAgent
window: (/windows|compatible/i.test(userAgent))
macOS: (/macintosh|mac os x/i.test(userAgent))
ios: (/iphone|Ipad/i.test(userAgent))
android: (/android/i.test(userAgent))
```
# 判断浏览器
```
var browserName = navigator.userAgent
IE: (/msie/i.test(browserName) && !/opera/.test(browserName))
FireFox: (/firefox/i.test(browserName))
chrome: (/chrome/i.test(browserName) && /webkit/i.test(browserName) && /mozilla/i.test(browserName))
Opera: (/opera/i.test(browserName))
safari: (/webkit/i.test(browserName) &&!(/chrome/i.test(browserName) && /webkit/i.test(browserName) && /mozilla/i.test(browserName))
```