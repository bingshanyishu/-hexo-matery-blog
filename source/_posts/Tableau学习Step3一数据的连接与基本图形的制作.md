---
title: Tableau学习Step3一数据的连接与基本图形的制作
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
abbrlink: 220202ac
date: 2022-02-02 21:06:59
summary: 
img:
password:
---
# Tableau学习Step3一数据的连接与基本图形的制作

## 一. 前言

> **本教程通过一个案例从浅到深来学习Tableau知识**



**案例概述**

![image-20220107213741875](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107213741875.png)

**Northwind公司的数据库架构**

![image-20220107213852171](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107213852171.png)



## 二. 商业理解

![image-20220107214010791](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107214010791.png)



## 三. Tableau中的数据连接和数据源

### 3.1 数据连接

![image-20220107214142880](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107214142880.png)



### 3.2 数据源

![image-20220107214200499](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107214200499.png)



### 3.3 数据模型

数据表

- 数据库中存储数据的具体实现方式,有真实的物理存储空间
- 可以通过对表的操作来实现用户对数据的操作

数据视图

- 通过数据表间的逻辑关系,通过代码来将一些表中的数据进行连接整理后形成的一个逻辑表
- 视图在物理存储上并不存在,所有的数据都来自于对相关表的读取
- 对视图中数据的改变(如果允许的话)都直接是对源数据表内容的修改
- 优点:减少冗余数据,节省空间
- 缺点:功能受限,读写效率度,用不到的数据也必须进行逻辑拼接



在2020年2月，Tableau在数据底层对其**数据模型**进行了重大的更新，主要分为了**物理层**和**逻辑层**

![image-20220107214425195](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107214425195.png)

**如今Tableau在多表数据时的处理方式**

![image-20220107214645442](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107214645442.png)



### 3.4 基于SQL的多表关联

可自定义SQL查询，编写了所需要的数据的SQL语言，大大简化了Tabeau直接对数据处理的方便性。

![image-20220107221110328](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107221110328.png)



### 3.5 多数据源的融合

不同的表可进行相互关联，实现不同表的数据的连接

![image-20220107221153750](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107221153750.png)



### 3.6 远程数据的提取与保存

#### 3.6.1 接口差异

Desktop版和 Public版的数据接口差异

![image-20220107215111490](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107215111490.png)



#### 3.6.1 文件类型

**Tableau常见的数据类型**

![image-20220107215307255](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107215307255.png)



## 四.Top监测表的制作

### 4.1 数据表汇总方式

分别将**公司名称，地区，城市，地址，客户ID**拖到行，将**total**拖入到列

![image-20220107220638750](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107220638750.png)



### 4.2 数据提取汇总方式

**实时**提取数据当数据源改变后，Tableau里连接的数据也会发生改变

若采用**数据提取**则当数据源改变后，Tableau里的连接的数据源也不会发生改变

![image-20220107220557763](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107220557763.png)



### 4.3 筛选器

**Tableau中的筛选器**

![image-20220107220733966](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107220733966.png)



### 4.4 参数

![image-20210908221421302](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20210908221421302.png)

## 五.近一步的分析需求

**需求**

- 对Topn客户的订单情况做历史数据的深入考察
- 在名单中加入总金额未达到Topn,但总订单数较多的客户，如历史订单数>=15
- 对上述信息形成动态监测界面,便于分析和观察

**细化**

![image-20220107221004605](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107221004605.png)



### 5.1 刻度值的编辑操作

![image-20210908223958933](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20210908223958933.png)



### 5.2 多个汇总值的考查

![image-20210908224458638](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20210908224458638.png)

![image-20210908224513082](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20210908224513082.png)

### 5.3 维度分层与维度钻取

![image-20210908224904379](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20210908224904379.png)

### 5.4 集合的使用

![image-20220107221336410](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20220107221336410.png)

### 5.5 绘制统计地图

![image-20210908225609947](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20210908225609947.png)

### 5.6 构建仪表板

![image-20210909093817782](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy03/image-20210909093817782.png)
