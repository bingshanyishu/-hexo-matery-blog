---
title: Tableau学习Step4一数据解释、异常值监测、参数使用、分析结果如何对外发布
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
abbrlink: 220202zc
date: 2022-02-02 21:36:59
summary:
img:
password:
---

# Tableau 学习 Step4 一数据解释、异常值监测、参数使用、分析结果如何对外发布

## 一. 前言

> **本教程通过一个案例从浅到深来学习 Tableau 知识**

![image-20220110160620085](https://img-blog.csdnimg.cn/img_convert/c2cf3ff5149030f58aae8d70e8cd1e65.png)

## 二. 为数据源添加数据

### 2.1 替换数据源

![img](https://img-blog.csdnimg.cn/img_convert/416e08d2f3529da4c7414aed2bd0cc5a.png)

### 2.2 并集追加

![image-20210909100639787](https://img-blog.csdnimg.cn/img_convert/532a47246976c8d10a1d675a07207c17.png)

### 2.3 提取后追加

![image-20210909100903676](https://img-blog.csdnimg.cn/img_convert/096136dc2a929bee76a35a09fcfa1a31.png)

**添加只有一个工作表的数据源**

## 三. 数据解释自动分析

![image-20210909102456650](https://img-blog.csdnimg.cn/img_convert/3fecfd272001c3ea19c5f9bb2d1ea11b.png)

![image-20210909102509932](https://img-blog.csdnimg.cn/img_convert/f0080243862b2f3522e63eb0f69f025a.png)

## 四. 异常值监测

### 4.1 参考线与参考区间

**对个体信心值中的异常值进行监测**

-   单纯的直方图或者箱图并不能完全满足需求,需要考虑将其和点图、参考线等工具相结合
-   点图
-   常量、单值、区间和分布
    -   填充方向和颜色渐变
    -   百分位数
-   箱图
    -   屏蔽正常范围的数据散点

![image-20220110163536506](https://img-blog.csdnimg.cn/img_convert/8abf24a3cb5f89f7e73a2c0a14b4daaa.png)

### 4.2 箱图

![image-20220110163616342](https://img-blog.csdnimg.cn/img_convert/22835cf17fb7fb58091d5c9626592e17.png)

## 五. 使用参数

![image-20210909110344978](https://img-blog.csdnimg.cn/img_convert/e58c9035e2fd6d777387d86170a07d64.png)

![image-20210909110414463](https://img-blog.csdnimg.cn/img_convert/fd5965210d24f0f693c46faebb46b8ad.png)

![image-20210909110454796](https://img-blog.csdnimg.cn/img_convert/92ebb16f54fff5974f617212c6dadfb5.png)

![image-20210909110529102](https://img-blog.csdnimg.cn/img_convert/d5a22adfe8516049c21435e292ecab10.png)

## 六. 其余统计分析

![image-20220110205937616](https://img-blog.csdnimg.cn/img_convert/2454004d66b790715fa8127076fcf0e8.png)

## 七. 分析结果的对外发布

![image-20220110210000220](https://img-blog.csdnimg.cn/img_convert/7d227ab7fded906454508225841f28e6.png)

### 7.1 离线打包

工作薄与打包工作簿，后者包括数据源

![image-20210909130107062](https://img-blog.csdnimg.cn/img_convert/fd7053172fdeacd67c60ad141c5fc359.png)

### 7.2 在线发布

![image-20210909131108758](https://img-blog.csdnimg.cn/img_convert/62540051b48de04a9b5aae7876e311d8.png)

## 八. 图表模板的应用

直接替换数据源

![image-20220110210116699](https://img-blog.csdnimg.cn/img_convert/3f07da856fb55d0f64ff7c85de8c504b.png)
