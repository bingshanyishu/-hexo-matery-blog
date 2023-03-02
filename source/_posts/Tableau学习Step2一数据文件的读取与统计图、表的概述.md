---
title: Tableau学习Step2一数据文件的读取与统计图、表的概述
author: Sankey
coverImg: /medias/banner/2.jpg
top: false
cover: false
toc: true
mathjax: false
tags:
  - Tableau学习
categories:
  - 技能之树
reprintPolicy: cc_by
abbrlink: 220202ab
date: 2022-02-02 21:06:48
summary: 
img:
password:
---
# Tableau学习Step2一数据文件的读取与统计图、表的概述

## 一. 前言

> 本教程通过一个案例从浅到深来学习Tableau知识

![image-20220107210139030](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20220107210139030.png)

**案例概述**：

![image-20220107211103857](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20220107211103857.png)



## 二. 文件读取



### 2.1 数据结构

![image-20220107211200274](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20220107211200274.png)

**统计分析方法,都是以关系型数据库的二维表作为基本数据结构的**

![image-20220107211253046](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20220107211253046.png)



### 2.2 标准格式文件读取

![image-20210906220446181](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906220446181.png)



### 2.3 非标准文件读取

![image-20210906220530127](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906220530127.png)

![image-20210906220734770](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906220734770-16418833090637.png)



### 2.4 数据透视表读取

![image-20210906220849722](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906220849722.png)

![image-20210906220916007](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906220916007.png)



### 2.5 并集文件与拼接文件

![image-20210906221033923](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906221033923.png)

![image-20210906221113063](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906221113063.png)



## 三. 编辑和整理数据

### 3.1 基本的数据整理操作

- 名称与重命名
- 更改数据类型: 数值、日期、字符、逻辑
- 字符型变量
    - 别名
    - 数值拆分

- 数值型变量
    - 数值分段(创建级)

- 创建
    - 新变量
    - 数据组
- 隐藏数据列



例：可使用创建计算字段来拆分列，如下图

```tableau
SPLIT函数按逗号来拆分name行
```

![image-20210906221424747](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906221424747.png)



## 四.维度与度量

![image-20210906221725627](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906221725627.png)



## 五.统计表的基本类型

### 5.1 表格的基本框架

![image-20210906222043916](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906222043916.png)



### 5.2 表格绘制的基本步骤

![image-20210906222748623](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906222748623.png)



### 5.3 叠加表

![image-20210906222208287](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906222208287.png)



### 5.4 交叉表

![image-20210906222335250](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906222335250.png)



### 5.5 嵌套表

![image-20210906222500552](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906222500552.png)



### 5.6 多层表

![image-20210906222609114](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906222609114.png)



### 5.7 复合表格

![image-20210906222643190](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906222643190.png)





## 六.泰坦尼克号数据的表格化分析

### 6.1 性别

![image-20210906224343447](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906224343447.png)



### 6.2 舱位

舱位操作同性别

![image-20210906224720648](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906224720648.png)



### 6.3 交叉表分析

![image-20210906224919554](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906224919554.png)

![image-20210906225724706](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210906225724706.png)



## 七.统计图的的基本类型

### 7.1 统计图的分类框架

- 统计图的分类方法有许多种,但作为数据分析和呈现的工具,最好使用和统计学体系最为贴近的方法对其加以分类
- 首先按照其呈现变量的数量,将统计图大致分为单变量图、双变量图、多变量图等
    随后再根据相应变量的测量尺度进行更细的区分
- Tableau中提供了一些新式的图形,他们并不完全符合标准的统计绘
    图要求,对这些图形的使用应当谨慎,注意不要因此冲淡分析主题



### 7.2 单个—分类变量

![image-20210907085804134](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210907085804134.png)

![image-20210907085635910](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210907085635910.png)



### 7.3 单个—数据变量

![image-20210907090336383](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210907090336383-164188336036130.png)



#### 7.3.1 直方图

![image-20210907090051290](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210907090051290-164188336197132.png)



#### 7.3.2 箱图

![image-20210907090308959](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210907090308959.png)



### 7.4 数据因变量

![image-20210907090754312](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210907090754312.png)

#### 7.4.1 条图

![image-20210907090558578](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210907090558578.png)

#### 7.4.2 点图

![image-20210907090633254](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210907090633254.png)

#### 7.4.3 线图

![image-20210907090718179](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210907090718179.png)



### 7.5 分类因变量

![image-20210907090848984](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210907090848984.png)

![image-20210907090902983](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210907090902983.png)



### 7.6 组合图

![image-20210907092505530](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210907092505530.png)

![image-20210907092411182](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy02/image-20210907092411182.png)





> 注：以上内容为报名的Tableau课程笔记，仅作为个人复习自用。如有侵权，请联系删除

