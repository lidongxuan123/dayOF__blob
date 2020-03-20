---
title: 关闭进程，释放进程占用的接口
date: 2019-11-22 09:01:29
tags: 关闭进程（服务启动过程中遇到接口被占用）
categories: 
- other(关闭进程，释放进程占用的接口)
---

# 关闭进程，释放接口
1. 查询接口占用的进程号
```
netstat -aon | findstr "8080"
```
2. 查询进程号被谁占用
```
tasklist | findstr "8080"
```
3. 关闭当前进程
```
taskkill /pid 进程号 /f
```