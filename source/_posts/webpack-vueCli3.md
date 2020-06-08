---
title: webpack_vueCli3
date: 2020-04-21 19:40:53
tags: vuecli3项目中webpack的配置
categories: webpack
---

# 项目中的使用
1. publicPath: 项目链接地址上添加的 
    例如： publicPath: "/ued"
    127.0.0.1:3000/ued
2. outputDir: 打包的文件输出路径，默认为dist
3. indexPath
4. filenameHashing: 打包后的文件夹不带hash字符串
5. productionSourceMap: 生产环境sourceMap,方便找出错误
6. lintOnSave: 警告的显示
7. configureWebpack: webpack配置
    configureWebpack.resolve.extensions: ['.js','.vue','.json']:当没有写文件名时按照这个优先级进行匹配
    configureWebpack.resolve.alias: 起别名
    configureWebpack.resolve.plugins: 引用第三方的插件
8. css:css配置
    css.extract:true :表示把文件中的css摘出来写到css文件里
    css.sourceMap: false:表示文件中的
9. devServer服务的配置
    devServer.proxy 设置前端跨域请求
10. pages 多页面的配置
    pages: {
        index:{
            entry: 入口文件
            template: 模板文件名
            filename: 生成文件名
            title:  模板中的标题
            chunks:  生成js css的名称
        }
    }