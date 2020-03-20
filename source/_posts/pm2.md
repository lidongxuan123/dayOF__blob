---
title: pm2
date: 2019-11-08 08:59:58
tags: PM2部署前端环境
categories: vmware web_Linux_部署
---

# 安装pm2(前提条件：linux已经安装好了node)
npm -install pm2 -g
## 启动express自动生成器中的项目
pm2 start node ./bin/www
## 运行过程中的日志
pm2 logs app
日志路径： root/.pm2/logs/app-out.log
![alt pm2运行过程中产生日志信息](/images/node/pm2_1/pm2_logs_1.png)

# 总结pm2
## pm2是什么
pm2是一个进程管理工具,可以用它来管理你的node进程，并查看node进程的状态，当然也支持性能监控，进程守护，负载均衡等功能
## pm2常用命令行
1. 启动进程：pm2 start bin/www 或 pm2 start app.js
2. 进程重命名： pm2 start app.js --name 别名
3.  添加进程/应用 watch： pm2 start bin/www --watch
4. 结束进程： pm2 stop + 进程名
5. 结束所有进程： pm2 stop all
6. 删除进程： pm2 delete + 进程名
7. 删除所有进程：pm2 delete all 
8. 列出所有进程： pm2 list
9. 查看pm2的日志： pm2 logs
10.
