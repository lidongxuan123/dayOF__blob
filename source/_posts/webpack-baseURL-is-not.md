---
title: webpack_baseURL_is_not
date: 2019-12-17 16:39:27
tags: webpack打包BASE_URL is not defined
categories: webpack
---

# 错误展示

```
CMD(错误)
ERROR in Template execution failed: ReferenceError: BASE_URL is not defined

ERROR in   ReferenceError: BASE_URL is not defined

```
```
打包文件HTML
Html Webpack Plugin:
<pre>
  ReferenceError: BASE_URL is not defined
  - default.html:95 
    E:/pimSelf_file/envament/project/public/default.html:95:11
  - default.html:98 module.exports
    E:/pimSelf_file/envament/project/public/default.html:98:3
  - index.js:284 Promise.resolve.then
    [project]/[html-webpack-plugin]/index.js:284:18
</pre>
```
# 解决方法 
1. 造成原因: 没有定义全局变量BASE_URL
2. 解决方法: 
```
 new webpack.DefinePlugin({
    'NODE_ENV': JSON.stringify(process.env.NODE_ENV),
    'BASE_URL': JSON.stringify('/')
}),
```
