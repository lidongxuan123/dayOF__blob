---
title: xterm Xshell.js写命令行的工具
date: 2020-06-08 10:58:07
tags: Xterm 
categories: 
- npm包知识
---

# Xterm 
XTerm是一个X Window System上的终端模拟器，用来提供多个独立的SHELL输入输出。

# 安装 
npm i xterm
# 使用
import {terminal} from "xterm"

#使用插件
npm i -S xterm-addon-web-links


import { Terminal } from 'xterm';
import { WebLinksAddon } from 'xterm-addon-web-links';

# 几个重要的插件
xterm-addon-attach:通过websocket连接到运行进程的服务器
xterm-addon-fit:使终端与包含元素相匹配
xterm-addon-search:添加搜索功能
xterm-addon-web-links:添加web链接检测和交互


