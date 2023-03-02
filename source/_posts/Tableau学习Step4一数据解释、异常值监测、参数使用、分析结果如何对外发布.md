---
title: Tableau学习Step4一数据解释、异常值监测、参数使用、分析结果如何对外发布
author: Sankey
coverImg: /medias/banner/1.jpg
top: false
cover: false
toc: true
mathjax: false
tags:
  - Tableau学习
categories:
  - 技能之树
reprintPolicy: cc_by
abbrlink: 220202ad
date: 2022-02-02 22:06:59
summary: 
img:
password:
---
# Tableau学习Step4一数据解释、异常值监测、参数使用、分析结果如何对外发布

## 一. 前言

> **本教程通过一个案例从浅到深来学习Tableau知识**

![image-20220110160620085](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20220110160620085.png)



### 1.1 消费者信心指数定义

**消费者信心**( Consumer Confidence or Consumer Sentiment)是指消费者根据国家或地区的经济发展形势,对**就业、收入、物价、利**
**率**等问题综合判断后得出的一种看法和预期·居民在决策家庭的开销,特别是购买诸如住宅、汽车等耐用商品时,是经过深思熟虑才决定的。不仅是以目前的经济条件为基础,同时结合了对未来收入、就业、物价、利率变动等因素的判断和预期理论体系最早由美国密歇根大学调查研究中心的乔治-卡通纳( GeorgeKatona)在上世纪40年代后期提出六十多年的时间己经充分验证了上述理论在**解释宏观经济现状时的有效性与合理性**



### 1.2 中国消费者信心指数的需求

- 中国经济的重要性逐渐增高
- 国外对中国官方统计数据的质疑持续存在
- 地方数据和全国数据的较大差异
- 过高和过低数据时的修正(这个全世界其实都一样)
- 官方统计信息对于商业分析需求的匹配度较差
- 第三方数据:一大堆烂番茄!



### 1.3 指数研究方法

调研的研究方法

![image-20220110205807653](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20220110205807653.png)

### 1.4 中国消费者信心指数研究问卷

![image-20220110162504604](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20220110162504604.png)

![image-20220110162528498](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20220110162528498.png)



**指数值的计算方法**

![image-20220110162621451](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20220110162621451.png)



### 1.5 分析需求

- 数据源可直接增添每月的新数据,且相应的图表均可分月浏览
- 对个体信心值中的异常值进行监测
- 展示不同群体的信心指数差异,并在图形中加汇参考线辅助分析
- 使用适当的工具展示开放题细节特征





## 二. 为数据源添加数据

### 2.1 替换数据源

![img](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/d42d2de2707346d24410bfa141a04b06.png)





### 2.2 并集追加

![image-20210909100639787](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20210909100639787.png)





### 2.3 提取后追加

![image-20210909100903676](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20210909100903676.png)

**添加只有一个工作表的数据源**





## 三. 数据解释自动分析

![image-20210909102456650](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20210909102456650.png)

![image-20210909102509932](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20210909102509932.png)







## 四. 异常值监测

### 4.1 参考线与参考区间

**对个体信心值中的异常值进行监测**

- 单纯的直方图或者箱图并不能完全满足需求,需要考虑将其和点图、参考线等工具相结合
- 点图
- 常量、单值、区间和分布
    - 填充方向和颜色渐变
    - 百分位数
- 箱图
    - 屏蔽正常范围的数据散点



![image-20220110163536506](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20220110163536506.png)





### 4.2 箱图

![image-20220110163616342](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20220110163616342.png)





## 五. 使用参数

![image-20210909110344978](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20210909110344978.png)

![image-20210909110414463](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20210909110414463.png)

![image-20210909110454796](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20210909110454796.png)

![image-20210909110529102](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20210909110529102.png)





## 六. 其余统计分析

![image-20220110205937616](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20220110205937616.png)

## 七. 分析结果的对外发布

![image-20220110210000220](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20220110210000220.png)

### 7.1 离线打包

工作薄与打包工作簿，后者包括数据源

![image-20210909130107062](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20210909130107062.png)

### 7.2 在线发布

![image-20210909131108758](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20210909131108758.png)





## 八. 图表模板的应用

直接替换数据源

![image-20220110210116699](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy04/image-20220110210116699.png)

