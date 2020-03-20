---
title: 解决git每次操作前都要输入用户名和密码。
date: 2019-11-21 15:59:19
tags: 解决git每次操作前都要输入用户名和密码。
categories: git 学习
---
# 解决git每次操作前都要输入用户名和密码。
1. 输入 git config --global credential.helper store执行后输入git pull，此时会重新需要输入一次用户名和密码，下次就不用输入了

```
git config --global credential.helper store
git pull
```