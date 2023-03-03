---
title: Tableau学习Step2一数据文件的读取与统计图、表的概述
author: Breezs
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

# Tableau 学习 Step2 一数据文件的读取与统计图、表的概述

## 一. 前言

> 本教程通过一个案例从浅到深来学习 Tableau 知识

![image-20220107210139030](https://img-blog.csdnimg.cn/img_convert/12fd1ebc8a4ffdd7e96a27cc339af1ff.png)

**案例概述**：

![image-20220107211103857](https://img-blog.csdnimg.cn/img_convert/597367330f3950ac259202da4eabb0ea.png)

## 二. 文件读取

### 2.1 数据结构

![image-20220107211200274](https://img-blog.csdnimg.cn/img_convert/9fa68f48000272284162d957065ded90.png)

**统计分析方法,都是以关系型数据库的二维表作为基本数据结构的**

![image-20220107211253046](https://img-blog.csdnimg.cn/img_convert/c5bb860890624f76c05fc045e6237d01.png)

### 2.2 标准格式文件读取

![image-20210906220446181](https://img-blog.csdnimg.cn/img_convert/b21ae2b9cd445d032075431a635508be.png)

### 2.3 非标准文件读取

![image-20210906220530127](https://img-blog.csdnimg.cn/img_convert/b052e0ac19d0945174614352cf9475b3.png)

![image-20210906220734770](https://img-blog.csdnimg.cn/img_convert/2702936fa4fecdf7b39897d32422e0db.png)

### 2.4 数据透视表读取

![image-20210906220849722](https://img-blog.csdnimg.cn/img_convert/4ac126307c560386c4122fea74f0b7bf.png)

![image-20210906220916007](https://img-blog.csdnimg.cn/img_convert/46e528ea1183128f79c675f4e8f3e6e5.png)

### 2.5 并集文件与拼接文件

![image-20210906221033923](https://img-blog.csdnimg.cn/img_convert/fd8f632e536d640ff2041e7dc4feaa47.png)

![image-20210906221113063](https://img-blog.csdnimg.cn/img_convert/db867c152601ff519d7cd1f86454ff40.png)

## 三. 编辑和整理数据

### 3.1 基本的数据整理操作

-   名称与重命名
-   更改数据类型: 数值、日期、字符、逻辑
-   字符型变量

    -   别名
    -   数值拆分

-   数值型变量

    -   数值分段(创建级)

-   创建
    -   新变量
    -   数据组
-   隐藏数据列

例：可使用创建计算字段来拆分列，如下图

```tableau
SPLIT函数按逗号来拆分name行
```

![image-20210906221424747](https://img-blog.csdnimg.cn/img_convert/58f35de316960bd2899105f9d0c86904.png)

## 四.维度与度量

![image-20210906221725627](https://img-blog.csdnimg.cn/img_convert/6ad61ed2a825744e0eeb2eb3ba77b1ea.png)

## 五.统计表的基本类型

### 5.1 表格的基本框架

![image-20210906222043916](https://img-blog.csdnimg.cn/img_convert/eaa3daa09d9f2e08a8eac9d737695d97.png)

### 5.2 表格绘制的基本步骤

![image-20210906222748623](https://img-blog.csdnimg.cn/img_convert/0ab1ab5dd2db7f3458073b7d43c4e618.png)

### 5.3 叠加表

![image-20210906222208287](https://img-blog.csdnimg.cn/img_convert/5b7b2e2cdef46920d0c66254b8173785.png)

### 5.4 交叉表

![image-20210906222335250](https://img-blog.csdnimg.cn/img_convert/c37eb30aee2f6fbb650264ce54c4002e.png)

### 5.5 嵌套表

![image-20210906222500552](https://img-blog.csdnimg.cn/img_convert/1f1815c4145b4afedde2917ee572ed9c.png)

### 5.6 多层表

![image-20210906222609114](https://img-blog.csdnimg.cn/img_convert/a7e12c62881be7a7ed7750e3c8a5d6e9.png)

### 5.7 复合表格

![image-20210906222643190](https://img-blog.csdnimg.cn/img_convert/4863b62c8b8650f57134b1ac0f762b96.png)

## 六.泰坦尼克号数据的表格化分析

### 6.1 性别

![image-20210906224343447](https://img-blog.csdnimg.cn/img_convert/4c56da4c96f07371b02b67d17f354a5f.png)

### 6.2 舱位

舱位操作同性别

![image-20210906224720648](https://img-blog.csdnimg.cn/img_convert/feb33755cf3750051c4a2c71f12d7b44.png)

### 6.3 交叉表分析

![image-20210906224919554](https://img-blog.csdnimg.cn/img_convert/d3fe86b8ab786ab8155695307ae71248.png)

![image-20210906225724706](https://img-blog.csdnimg.cn/img_convert/371fa80740844a555b394ccb178e6d5d.png)

## 七.统计图的的基本类型

### 7.1 统计图的分类框架

-   统计图的分类方法有许多种,但作为数据分析和呈现的工具,最好使用和统计学体系最为贴近的方法对其加以分类
-   首先按照其呈现变量的数量,将统计图大致分为单变量图、双变量图、多变量图等
    随后再根据相应变量的测量尺度进行更细的区分
-   Tableau 中提供了一些新式的图形,他们并不完全符合标准的统计绘
    图要求,对这些图形的使用应当谨慎,注意不要因此冲淡分析主题

### 7.2 单个—分类变量

![image-20210907085804134](https://img-blog.csdnimg.cn/img_convert/4c597a4f405fc1630ffb97f201fa1a3f.png)

![image-20210907085635910](https://img-blog.csdnimg.cn/img_convert/d2e7549e00e0ecb7f7d3ef7d7f6ea6e9.png)

### 7.3 单个—数据变量

![image-20210907090336383](https://img-blog.csdnimg.cn/img_convert/c6c4c2d074d4aa4de2b7f81c29dc31ef.png)

#### 7.3.1 直方图

![image-20210907090051290](https://img-blog.csdnimg.cn/img_convert/c1c063bdeb3d5475b4fe39912dd749ea.png)

#### 7.3.2 箱图

![image-20210907090308959](https://img-blog.csdnimg.cn/img_convert/e9c9fb33b8fd46fdfc577d39ce5b4282.png)

### 7.4 数据因变量

![image-20210907090754312](https://img-blog.csdnimg.cn/img_convert/c960f3e5d67a312dc3029098e06bbb66.png)

#### 7.4.1 条图

![image-20210907090558578](https://img-blog.csdnimg.cn/img_convert/842e2a2fc96762301b53019bebc872c5.png)

#### 7.4.2 点图

![image-20210907090633254](https://img-blog.csdnimg.cn/img_convert/a5156da3288f8731d42e1ed4a3852d82.png)

#### 7.4.3 线图

![image-20210907090718179](https://img-blog.csdnimg.cn/img_convert/20546152bbb249acbda146a49c4f7310.png)

### 7.5 分类因变量

![image-20210907090848984](https://img-blog.csdnimg.cn/img_convert/6ad141abe2489b184a51862113023bb9.png)

![image-20210907090902983](https://img-blog.csdnimg.cn/img_convert/61d7b54ad3a6cc1d02d018de6540094b.png)

### 7.6 组合图

![image-20210907092505530](https://img-blog.csdnimg.cn/img_convert/574d2e6c1b98afa6180245ca89f1e994.png)

![image-20210907092411182](https://img-blog.csdnimg.cn/img_convert/47bf01b0bd4928e9b5dd01bf20747b88.png)

> 注：以上内容为报名的 Tableau 课程笔记，仅作为个人复习自用。如有侵权，请联系删除
