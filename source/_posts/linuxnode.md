---
title: linux 上安装node
date: 2019-11-08 09:07:53
tags: linux 上安装node
categories: linux node安装升级卸载
---

# linux上安装node
## 安装
1. curl –sL https://rpm.nodesource.com/setup_10.x |bash -
2. yum install –y nodejs  (安装nodejs)
3. node –v  /   npm –v  (验证安装node是否成功) 
4. whereis node (查看node安装的位置)

## 更新（升级）
1. npm install -g n (n是nodejs管理工具)
2. n latest (安装node最新版)
3. n 版本号(安装指定的版本)
 
## 卸载
1. yum remove nodejs npm -y
2. 手动删除文件的残留 

# 安装过程中遇到的问题
1. /var/run/yum.pid已被锁定，PID为2925的另一个程序正在运行
![alt linux上安装node](/images/node/node_1/linux_node_install.png)




