---
title: express-Learn & express框架学习
date: 2019-12-17 09:10:39
tags: express框架学习
categories: 
- express框架学习
---

# Express学习
1. 获取请求中相关数据（req)
> req.app: 当callback为外部文件时，用req.app访问express的实例
> req.baseUrl: 获取路由当前安装的URL路径
> req.body: post请求体数据
> req.hostname/req.ip: 主机名和IP
> req.originalUrl: 获取原始请求url
> req.params: 获取路由的parameters
> req.path: 获取请求路径
> req.protocol: 获取协议类型
> req.query: 获取get请求的数据
> req.route: 获取当前匹配的路由
> req.accepts:可接受的请求文档类型

# 数据返回
> res.app: 
> res.append: 追加指定HTTP头
> res.set()在res.append()后将重置之前设置的头
> res.cookie(name, value, [option]): 设置Cookie
> res.clearCookie():清除cookie
> res.download(): 下载文件
> res.get():返回指定的http头
> res.sendFile(path, options, fn): 发送文件
> res.status: 设置http状态码
> res.type: 设置content-type的mime类型

# express知识点
1. 静态资源托管
> express.static(root, [options]) *root为静态资源所在的目录，options是可选的*
> options包含：
ap.use("/xxx",express.static(path.join(__dirname),options))
a. dotfiles: 对以点开头的文件的请求处理  allow没有特殊处理，允许。deny拒绝对点文件的请求，回复403 默认ignore
b. extensions：
设置文件扩展名回退：如果找不到文件，请搜索具有指定扩展名的文件并提供找到的第一个文件。
示例：['html', 'htm']。比如设置html后请求的是/views/a.asd，它在里面找不到相关文件就会返回/views/index.html文件
默认false:关闭这个功能
['htm', 'html']：如果找不到请求的文件则返回第一个找到的htm或者html文件
c. fallthrough: 打印并返回具体的错误
false:返回具体错误
默认true:不打印和返回具体错误
d. immutable：
immutable在Cache-Control响应头中启用或禁用该指令。
如果启用，maxAge还应指定该选项以启用缓存。
该immutable指令将阻止受支持的客户端在maxAge选项的生命周期内发出条件请求，以检查文件是否已更改
true：客户端来第二次请求的时候返回文件未更改，且在maxAge设定的时间内不再检查服务端文件是否更改，直接调取本地的缓存
默认false: 相反
e.index:发送指定的目录索引文件。
默认'index.html':如果请求一个目录，默认返回index.html文件
false:禁用目录索引
f. lastModified:
设置文件在系统中的最后修改时间到Last-Modified头部
默认true:开启
false:关闭,
G. maxAge：设置Cache-Control标头的max-age属性，设置缓存文件的最大过期时间
如果过期就重新请求，而不是调用缓存
以毫秒为单位或字符串
H. redirect：当路径名是目录时，重定向到尾随“/”（这个我不太懂，有没有大佬提示的）
默认true：开启
false：关闭
I. setHeaders：设置响应头
function (res, path, stat) {
    res.set('x-timestamp', Date.now())
  }
其中
res，响应对象。
path，正在发送的文件路径。
stat，正在发送的文件的对象。
2. 模板引擎
> app.engine(ext, callback)
> app.engine('jade', require('jade').__express)
> app.engine('html', require('ejs').__renderFile)
