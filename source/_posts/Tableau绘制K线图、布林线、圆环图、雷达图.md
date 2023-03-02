---
title: Tableau绘制K线图、布林线、圆环图、雷达图
author: Sankey
coverImg: /medias/banner/2.jpg
top: false
cover: false
toc: true
mathjax: false
tags:
    - Tableau绘图
categories:
    - 技能之树
reprintPolicy: cc_by
abbrlink: 220203ab
date: 2022-02-03 00:38:48
summary:
img:
password:
---

# Tableau 绘制 K 线图、布林线、圆环图、雷达图

## 一. K 线图

![image-20211004105719192](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004105719192.png)

### 1.1 导入数据源

![image-20211004093731975](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004093731975.png)

### 1.2 拖拽字段

将【日期】托到列这一栏，并将其改为年/月/日类型

![image-20211004094127869](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004094127869.png)

将【最低】拖到行这一栏。将【日期】拖到筛选，筛选字段设置为**日期范围**，日期大体设置为 2020/6/11~~2010/9/7（参考范围，可自己设置）

![image-20211004100428576](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004100428576.png)

### 1.3 创建计算字段

创建计算字段，名字为**高低差**，公式为**[最高]-[最低]**，创建之后将其拖到标记下的**大小**，并将将其改成**甘特条形图**

![image-20211004102047269](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004102047269.png)

### 1.4 编辑轴

分别将【开盘】，【收盘】拖到**详细信息**，之后编辑轴，设定范围从**2300 到 2800**

![image-20211004101724808](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004101724808.png)

### 1.5 做双图

创建计算字段，将其命名为**收开盘价差**，公式为**[收盘]-[开盘]**

![image-20211004101955928](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004101955928.png)

将【开盘】拖到行这一栏，将【收开盘价差】拖到标记下**总和（开盘）**的**大小**标记下

![image-20211004102454517](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004102454517.png)

之后**双轴、同步轴**

![image-20211004104126831](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004104126831.png)

### 1.6 修改颜色（涨跌）

将**总和（最低）**的大小减小，之后创建计算字段，

![image-20211004104444106](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004104444106.png)

名字为**涨跌情况**，公式为**IIF([收盘]>[开盘],'涨','跌')**，将其拖拽到**总和（开盘）**下的颜色标记中，并按要求设置颜色，，这里将跌设置为红色，涨设置为蓝色。

![image-20211004104718805](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004104718805.png)

最后调整对应坐标轴，标题这些即可

![image-20211004105112673](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004105112673.png)

## 二. 布林线

![image-20211004125116885](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004125116885.png)

### 2.1 导入数据源

![image-20211004110025776](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004110025776.png)

### 2.2 拖拽字段

将【日期】拖拽到列这一栏，将其格式设置为**天**，将【收盘】拖拽到行这一栏，将其度量设置为平均值。将【日期】拖拽到筛选器中，设定筛选范围为**2019/5/25~~2020/9/7**..

![image-20211004110759168](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004110759168.png)

修改坐标轴范围为最小**2000**

![image-20211004111948071](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004111948071.png)

### 2.3 创建参数

鼠标右键 创建参数 参数名字为移动窗口，数据类型设置为整数，允许的值改为范围，，值范围改为最小值：1，最大值：30，步长：1，，之后**显示参数控件**

![image-20211004111534911](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004111534911.png)

### 2.4 快速表计算

将行上的平均值（收盘）进行**移动平均**的快速表计算，将其拖到**数据-度量**中并进行编辑，

修改名字为**MA**，将其公式中的**-2 改为-移动窗口**

![image-20211004113240901](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004113240901.png)

之后将 MA 替换原来的平均值（收盘），再将【收盘】将其拖到坐标轴中 。并重新设置坐标轴范围

![image-20211004113349796](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004113349796.png)

![image-20211004122241979](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004122241979.png)

### 2.5 创建 SD 计算字段与参数

创建计算字段，名字为 SD，公式为**WINDOW_STDEV(AVG([收盘]),-移动窗口,0)**

![image-20211004122607550](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004122607550.png)

创建参数，名字为 SD 倍数，，数据类型为浮点，当前值为 1，显示格式设置为一位小数，允许的值为范围，最小值为 1，最大值为 3.。最后创建完毕后显示参数控件。

![image-20211004122840399](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004122840399.png)

### 2.6 创建上轨与下轨

创建计算字段，名字为 UP，公式为[MA]+[SD 倍数]\*[SD]

创建计算字段，名字为 DOWN，公式为[MA]-[SD 倍数]\*[SD]

![image-20211004123344081](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004123344081.png)

### 2.7 添加报警设定

将度量值下的【收盘】度量改成平均值，拖到最右边，再同步轴，然后去掉这个轴

![image-20211004123651926](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004123651926.png)

创建计算字段

名字为**是否报警**

公式为：**IIF(AVG([收盘])<UP AND AVG([收盘])>[DOWN],FALSE,TRUE)**

![image-20211004124106084](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004124106084.png)

将其拖到标记中的**平均值（收盘）**中的颜色里，，调节颜色与不透明度，，将**平均值（收盘）**的不透明度设置为 100%，将度量值的颜色设置为 50%，再更改各线的颜色，增加美观与辨别度

![image-20211004124738566](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004124738566.png)

## 三. 圆环图

![image-20211004135308267](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004135308267.png)

有的版本没有记录数这个字段，这里提供了两种绘制方法，不过思路是一样的。

### 3.1 导入数据源

示例超市

![image-20211004125459893](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004125459893.png)

### 3.2 步骤（有记录数）

#### 3.2.1 创建饼图

将【类别】拖到标记下的颜色中，将其改成**饼图**，将记录数拖拽到标记下的**角度**（要改成饼图后才有）

![image-20211004133705060](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004133705060.png)

#### 3.3.2 创建双图

将【记录数】拖拽到行这一栏，并再复制一个，将两个【记录数】的度量改成最小值。移除第二个图的类别标记

![image-20211004134230196](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004134230196.png)

#### 3.2.3 修改大小

将两个图，双轴，再同步轴

将视图改成**整个视图**，将标记下的**最小（记录数）**大小调大，标记下的**最小（记录数）（2）**大小稍微小点，并将其颜色改成**白色**

![image-20211004134649488](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004134649488.png)

#### 3.2.4 添加标签

将【类别】、【记录数】拖到标记下的**最小（记录数）**的标签中，调节字体，字号大小

将【记录数】拖到标记下的**最小（记录数）**的标签中，调节字体，字号大小，标签再加**总数**

![image-20211004135244360](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004135244360.png)

## 3.3 步骤（无记录数）

### 3.3.1 创建饼图

将【类别】拖到标记下的颜色中，将其改成**饼图**，将类别拖拽到标记下的**角度**（要改成饼图后才有），将其度量改成计数

![image-20211004135425514](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004135425514.png)

### 3.3.2 创建双图

将【类别】拖拽到行这一栏，并再复制一个，将两个【类别】的度量改成计数。对两者进行快速表计算——排序

移除第二个图的类别标记

### 3.3.3 其余操作类似

## 四. 雷达图

![image-20211004165333756](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004165333756.png)

### 4.1 导入数据源

![image-20211004153428151](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004153428151.png)

转置后更改名称

![image-20211004153703915](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004153703915.png)

![image-20211004153829515](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004153829515.png)

### 4.2 创建计算字段

（1）创建计算字段：

名字为**路径**

公式为：

```
CASE [性质]
WHEN '易抽取性' then 1
WHEN '粉尘量' then 2
WHEN '分层情况' then 3
WHEN '平整性' then 4
WHEN '厚度' then 5
WHEN '细腻度' then 6
WHEN '柔软度' then 7
WHEN '韧性' then 8
ELSE 9
END
```

![image-20211004162139852](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004162139852.png)

（2）创建计算字段，

名字为**角度**

公式为：

```
IF [路径]=9 THEN 0
ELSE -([路径]-1)*2*PI()/8
END
```

![image-20211004162317467](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004162317467.png)

(3)创建计算字段

名字分别为 X,Y

X：公式：`[大小]*COS([角度])`

Y：公式：`[大小]*SIN([角度])`

![image-20211004162600867](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004162600867.png)

### 4.3 拖拽字段

将 X 拖拽到列这一栏，Y 拖拽到行这一栏，将 F1 拖拽到标记下的颜色中，将其类型有**自动**改成**线**，将【路径】拖拽到标记下的**路径**，，最后将取消聚合度量（菜单栏中的**分析**--->**聚合度量取消打勾**）

![image-20211004162935587](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004162935587.png)

这时基本雏形就出来了

![image-20211004163328185](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004163328185.png)

### 4.4 添加标签

为了使标签位于最外层，可直接在外层点手动加，但显得很 LOW，这里才有创建计算字段来生成。

（1）创建计算字段

名字为性质标签

公式为：`if [大小]=5 THEN [性质] END`

![image-20211004163547459](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004163547459.png)

（2）创建计算字段

名字为数据标签

公式为：

`CASE [F1]`
`WHEN '产品A' THEN [大小]`
`WHEN '产品B' THEN [大小]`
`WHEN '产品C' THEN [大小]`
`END`

![image-20211004163709423](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004163709423.png)

（3）拖拽标签

复制行上的 Y，创建双图

将【性质标签】拖拽到标记下的总和(Y)(2)中的标签中

将【数据标签】拖拽到标记下的总和(Y)中的标签中，将数据标签类型改成**离散**，点击标签，勾选**允许标签覆盖其他标记**复选框

![image-20211004164603884](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004164603884.png)

### 4.5 去除坐标轴

将坐标轴去掉，也可添加筛选器来筛选产品，以方便观看。

![image-20211004165017295](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004165017295.png)

### 4.6 调整多余数据，颜色

将**易抽取性**中多余的数据隐藏掉（点击多余的数据，鼠标右键，将**标记标签改成从不显示**），将 5 个外围圆的颜色设置为灰色。

![image-20211004164530985](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004164530985.png)
