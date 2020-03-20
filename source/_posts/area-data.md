---
title: area-data 地址数据
date: 2019-12-23 11:09:30
tags: area-data-vue 写路径
categories: 
- npm包知识
---

# 安装
> npm install area-data --save

# 导入
// v5之前的版本
> import AreaData from 'area-data';
// v5及之后的版本
> import { pca, pcaa } from 'area-data';
// 可以根据需要按需引入：
> import PCA from 'area-data/pca'; 
> import PCAA from 'area-data/pcaa'; 

> pca['86'] // 等同于 AreaData['86']
// 所有省份：{'110000': '北京市', '120000': '天津市', '130000': '河北省', ...}

> pcaa['130000'] // 等同于 AreaData['130000']
// 对应省份的所有城市：{'130100': '石家庄市', '130200': '唐山市', '130300': '秦皇岛市', ...}



