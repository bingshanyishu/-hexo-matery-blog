---
title: Tableau怎么制作专业图表图
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
abbrlink: 220205ba
date: 2022-02-05 00:13:48
summary:
img:
password:
---

# Tableau 怎么制作专业图表

## 一. 统计表

### 1.1 不同种类的图表风格

**商业周刊的图表风格**

![image-20220202222959727](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202222959727.png)

**经济学人的图表风格**

![image-20220202223020732](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202223020732.png)

**华尔街日报的图表风格**

![image-20220202223045378](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202223045378.png)

其他媒体的图表风格

![image-20220202223104232](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202223104232.png)

### 1.2 专业图表的特点

![image-20220202223143645](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202223143645.png)

### 1.3 结论

风格统一，减少无关修饰

### 1.4 统计表的基本架构

![image-20220202223227663](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202223227663.png)

### 1.5 图表中的文字设定

-   注意：在图表中，文字往往处于从属地位，其格式不可喧宾夺主！
-   文字的优缺点
    -   缺点：线性阅读，理解速度较慢，量大时容易让人失去耐心
    -   优点：信息密度大，不容易产生歧义
-   在图表中如何合理利用文字
    -   利用其优点：用简短文字点明页面中心论点（标题或注解均可）
    -   弥补其缺点
        -   让文字变得有美感，让人亲近
        -   通过排版等方式将文字直观、有条理地组织起来，使之更容易理解
        -   控制文字总量，不同级别的大小有层次感

**文字的样式**

-   文字的字号
    -   现场演示：保证最后一排观众也能看清正文最小字号
    -   屏幕阅读：界面缩放至 60％，应当保证在对角线长度距离外也能看淸楚
    -   打印版本：应当至少使用 10 磅／五号字号
-   文字的效果

    -   使用深色背景＋白色文字，或者浅色背景＋黑色文字，然后使用其他颜色作为强调色
    -   尽量不要使用各种图片变色填充和文字特效
    -   行距：1.2－1.5 倍可以缓解密集文字的视觉压力
    -   对齐：视情况使用居中对齐、两端对齐

-   有衬线字体（ Serif）
    -   强调字母笔划的开始及结束，在笔画开始／结束的地方有额外的装饰，而且笔画的粗细会有所不同
    -   突出的是整个 word，而非单一字母
    -   ·易读性较高，但排版时容易出现行／列等情况
    -   中文字体很难按此分类严格归类
-   Garamond：圆润，古典优雅，非常适合显示大量文字
-   Times new roman：字母宽度差別小，应用范围广，不适合做标题
-   宋体：使用广泛的印刷体，笔画细，阅读性好，但不适合做标题

    -   SimSun ＝宋体， Mingliu ＝细明体

-   无村线字体（ Sans serif）：随印刷业的排版需求发展而来
    -   笔画的粗细差不多，小字体场合更容易阅读
    -   突出的是每一个字母
-   无衬线字体更加端正大气，往往是商业图表的首选
-   Arial：平实无个性，但也不会犯错，标题和正文均可使用
-   黑体：最早的无衬线中文字体，很醒目，但打印效果稍差
-   雅黑：平实，小字可读性很好，用做标题时冲击力不足
-   幼圆：比雅黑更细弱一些，更适合于正文

### 1.6 突破默认设定

**文字设定**

![image-20220202230356390](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202230356390.png)

**边框设定**

![image-20220202230413120](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202230413120.png)

## 二. 统计图

### 2.1 统计图的信息维度

![image-20220202224034978](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224034978.png)

![image-20220202224101825](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224101825.png)

### 2.2 配色方案

#### 2.2.1 从调色板开始

![image-20220202224147021](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224147021.png)

#### 2.2.2 颜色对比

![image-20220202224221257](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224221257.png)

#### 2.2.3 取色法

**三色组取色**

![image-20220202224314432](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224314432.png)

**分裂互补三色组**

![image-20220202224336992](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224336992.png)

类似取色

![image-20220202224400000](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224400000.png)

**调整亮度取色**

![image-20220202224444411](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224444411.png)

#### 2.2.3 常见配色方案

-   纯色
    -   素材选择受限，要求有很高的设计水平和绘图能力
-   单色
    -   给人谨慎、专业的感觉，商务咨询报告和商务图表报告中常见
-   双色
    -   较常见的配色方案，商业周刊的红蓝图表最经典
    -   互补色时，冷色做主色，小范围使用暖色做强调色
    -   更常见的是色轮上间隔 120° 的配色方式，这样对比仍然明显，但更和谐
-   多色
    -   以四色相的居多
    -   在韩系公司中尤为多见，看起来鲜艳活泼，但实际上重点不突出，很容易
    -   阅读疲劳

### 2.3 如何定义颜色系

![image-20220202224622879](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224622879.png)

### 2.3 案例

![image-20220202224647354](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224647354.png)

![image-20220202224702639](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224702639.png)

![image-20220202224717551](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224717551.png)

![image-20220202224730336](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224730336.png)

### 2.4 自定义颜色

![image-20220202224812156](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224812156.png)

### 2.5 自定义边界

![image-20220202224924133](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224924133.png)

### 2.6 自定义形状

![image-20220202224953082](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202224953082.png)

### 2.7 自定义图形框架

![image-20220202225007874](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202225007874.png)

## 三. 仪表板

### 3.1 版面设计四大原则

![image-20220202225037658](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202225037658.png)

#### 3.1.1 接近

![image-20220202225334896](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202225334896.png)

#### 3.1.2 对齐

![image-20220202225102330](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202225102330.png)

#### 3.1.3 重复

![image-20220202225131095](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202225131095.png)

#### 3.1.4 对比

![image-20220202225154538](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202225154538.png)

### 3.2 仪表板的设计

#### 3.2.1 仪表板的作用

![image-20220202225542495](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202225542495.png)

#### 3.2.2 设计的要点

![image-20220202225658891](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202225658891.png)

#### 3.2.3 注意点

![image-20220202225751072](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202225751072.png)

### 3.3 实践：冬小麦状况监测

#### 3.3.1 需求分析

![image-20220202230049387](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202230049387.png)

#### 3.3.2 数据展示工具分析

![image-20220202230321564](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202230321564.png)

#### 3.3.3 版面设计需求分析

![image-20220202230226550](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202230226550.png)

#### 3.3.4 仪表板需求细化

![image-20220202230252979](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202230252979.png)
