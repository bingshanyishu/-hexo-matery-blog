---
title: Tableau学习Step3一数据的连接与基本图形的制作
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
abbrlink: 220202ac
date: 2022-02-02 21:06:59
summary:
img:
password:
---

# Tableau 学习 Step3 一数据的连接与基本图形的制作

## 一. 前言

> **本教程通过一个案例从浅到深来学习 Tableau 知识**

**案例概述**

![image-20220107213741875](https://img-blog.csdnimg.cn/img_convert/d10335c64bbc3cbfde57bf98ee3bd4d9.png)

**Northwind 公司的数据库架构**

![image-20220107213852171](https://img-blog.csdnimg.cn/img_convert/f996d9b94e7ed7bbe697d018737f8395.png)

## 二. 商业理解

![image-20220107214010791](https://img-blog.csdnimg.cn/img_convert/63afd856ace7e04570caf09a7faa7d4b.png)

## 三. Tableau 中的数据连接和数据源

### 3.1 数据连接

![image-20220107214142880](https://img-blog.csdnimg.cn/img_convert/d7dc32d79920575e40294e42288e1a61.png)

### 3.2 数据源

![image-20220107214200499](https://img-blog.csdnimg.cn/img_convert/ec5bb928a8c1037c51ccd0b2529f249e.png)

### 3.3 数据模型

数据表

-   数据库中存储数据的具体实现方式,有真实的物理存储空间
-   可以通过对表的操作来实现用户对数据的操作

数据视图

-   通过数据表间的逻辑关系,通过代码来将一些表中的数据进行连接整理后形成的一个逻辑表
-   视图在物理存储上并不存在,所有的数据都来自于对相关表的读取
-   对视图中数据的改变(如果允许的话)都直接是对源数据表内容的修改
-   优点:减少冗余数据,节省空间
-   缺点:功能受限,读写效率度,用不到的数据也必须进行逻辑拼接

在 2020 年 2 月，Tableau 在数据底层对其**数据模型**进行了重大的更新，主要分为了**物理层**和**逻辑层**

![image-20220107214425195](https://img-blog.csdnimg.cn/img_convert/2f5accb54414e16077a22b2a19e0bd9a.png)

**如今 Tableau 在多表数据时的处理方式**

![image-20220107214645442](https://img-blog.csdnimg.cn/img_convert/11ce1e8452d96debfc66dd01abaf53d8.png)

### 3.4 基于 SQL 的多表关联

可自定义 SQL 查询，编写了所需要的数据的 SQL 语言，大大简化了 Tabeau 直接对数据处理的方便性。

![image-20220107221110328](https://img-blog.csdnimg.cn/img_convert/67336919bad0fa0171cd766b4dabed87.png)

### 3.5 多数据源的融合

不同的表可进行相互关联，实现不同表的数据的连接

![image-20220107221153750](https://img-blog.csdnimg.cn/img_convert/826907061d12768c9b5bd59d3442209e.png)

### 3.6 远程数据的提取与保存

#### 3.6.1 接口差异

Desktop 版和 Public 版的数据接口差异

![image-20220107215111490](https://img-blog.csdnimg.cn/img_convert/05da69bb5ef39c5a520eecd166fbefb0.png)

#### 3.6.1 文件类型

**Tableau 常见的数据类型**

![image-20220107215307255](https://img-blog.csdnimg.cn/img_convert/46dcf050e745d5b643cf0496f882a521.png)

## 四.Top 监测表的制作

### 4.1 数据表汇总方式

分别将**公司名称，地区，城市，地址，客户 ID**拖到行，将**total**拖入到列

![image-20220107220638750](https://img-blog.csdnimg.cn/img_convert/59666dafc38a96390b37e6637377bb2b.png)

### 4.2 数据提取汇总方式

**实时**提取数据当数据源改变后，Tableau 里连接的数据也会发生改变

若采用**数据提取**则当数据源改变后，Tableau 里的连接的数据源也不会发生改变

![image-20220107220557763](https://img-blog.csdnimg.cn/img_convert/4edc20d7c16c300b5ad4bafe61b0551d.png)

### 4.3 筛选器

**Tableau 中的筛选器**

![image-20220107220733966](https://img-blog.csdnimg.cn/img_convert/a27259654875a6360e63563cfc2cbadf.png)

### 4.4 参数

![image-20210908221421302](https://img-blog.csdnimg.cn/img_convert/6f919b892ba8bd67c81b367cebf386f6.png)

## 五.近一步的分析需求

**需求**

-   对 Topn 客户的订单情况做历史数据的深入考察
-   在名单中加入总金额未达到 Topn,但总订单数较多的客户，如历史订单数>=15
-   对上述信息形成动态监测界面,便于分析和观察

**细化**

![image-20220107221004605](https://img-blog.csdnimg.cn/img_convert/ec9eb2ebc210253cc6cb8abc876c0f42.png)

### 5.1 刻度值的编辑操作

![image-20210908223958933](https://img-blog.csdnimg.cn/img_convert/ef44e20e633e55d52d936f8e6f56f2ec.png)

### 5.2 多个汇总值的考查

![image-20210908224458638](https://img-blog.csdnimg.cn/img_convert/7f27bd5a1674a7ac08345835c1804fdc.png)

![image-20210908224513082](https://img-blog.csdnimg.cn/img_convert/0ca956efda125094e0b10060f5d5a8ea.png)

### 5.3 维度分层与维度钻取

![image-20210908224904379](https://img-blog.csdnimg.cn/img_convert/c6ac6b9dfb38a5703c0508b0749e205e.png)

### 5.4 集合的使用

![image-20220107221336410](https://img-blog.csdnimg.cn/img_convert/3d7b60e031fdd759a33657c5611ce612.png)

### 5.5 绘制统计地图

![image-20210908225609947](https://img-blog.csdnimg.cn/img_convert/b94d6baf8a0dd64812da47b5bd98c0e3.png)

### 5.6 构建仪表板

![image-20210909093817782](https://img-blog.csdnimg.cn/img_convert/703c98bab8e3d1092f7fcc15c1d61e2a.png)
