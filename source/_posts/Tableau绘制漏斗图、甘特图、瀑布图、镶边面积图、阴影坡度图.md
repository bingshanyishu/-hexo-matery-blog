---
title: Tableau绘制漏斗图、甘特图、瀑布图、镶边面积图、阴影坡度图
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
abbrlink: 220203aa
date: 2022-02-02 21:06:48
summary: Tableau到底如何绘制漏斗图、甘特图、瀑布图、镶边面积图、阴影坡度图、漏斗图
img:
password:
---

# Tableau 绘制漏斗图、甘特图、瀑布图、镶边面积图、阴影坡度图

## 一. 漏斗图

![image-20210915105147655](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915105147655.png)

**数据源**

![image-20220202163137490](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20220202163137490.png)

### 1.1 分色直条漏斗图

（1）导入数据

（2）将【数量】拖到行这一栏，将【阶段】拖到标记下的颜色选项卡吗，之后对数量进行降序排列。![image-20210914204947551](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210914204947551.png)

（3)把【数量】拖到标记下的大小选项卡，**视图**设置为**整个视图**

![image-20210914205145965](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210914205145965.png)

（4）把【阶段】，【数量】拖到标签选项卡，并对数量进行快速表计算——合计百分比。

![image-20210914205550841](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210914205550841.png)

（5）下面的图形由于太少而导致无法显示标签，对此可手动的选择，添加注释。（当然，为了美观，也可以选择不加）

![image-20210914205943824](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210914205943824.png)

### 1.2 同色斜边框漏斗图

（1）导入数据

（2）将【数量】拖到行这一栏，将【阶段】拖到标记下的颜色选项卡吗，之后对数量进行降序排列。并将“标记”下的**自动**改为**区域**

![image-20210914210440979](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210914210440979.png)

（3）重复列一栏的【数量】，并将左边图的坐标轴倒序

![image-20210914210640460](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210914210640460.png)

（4）将图表颜色不透明度改成 100%，鼠标右键设置格式，将边界的列分隔符改成无

![image-20210914210934112](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210914210934112.png)

（5）去掉坐标轴，并为图表添加标签，左侧添加【阶段】，右侧添加【数量】的百分比。并调整相应得大小，位置。

![image-20210914222922042](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210914222922042.png)

### 1.3 分条彩色漏斗图

（1）导入数据

（2）将【数量】拖到行这一栏，将【阶段】拖到标记下的颜色选项卡吗，之后对数量进行降序排列。把【阶段】拖到标记下得**颜色**。

![image-20210914223428455](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210914223428455.png)

（3）复制【数量】这一栏，将【数量 2】标记下的自动改为**线**，【数量 1】标记下的自动改为**条形图**，并合并**双轴**，再**同步轴**

![image-20210914223930082](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210914223930082.png)

（4）同理，再做一个相同的图形

![image-20210914224058654](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210914224058654.png)

（5)将第一个图形的轴倒序，并对图形鼠标右键——设置格式，将边界下的列分隔符改成无（以去掉合并图形中间的线），之后再去掉图形的坐标轴。

![image-20210914224429986](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210914224429986.png)

（6）将【阶段】拖到【数量 2】的标记下的**标签**中，【数量】拖到【数量 4】的标记下的**标签**中。并快速表计算——**合计百分比**。调整相应的大小，位置。

![image-20210914225102945](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210914225102945.png)

（7）如果不想要边缘的线，也可以删除两个线图所对应栏的【数量】，然后添加标签，并将此时标签左侧图设置为偏右/中，右侧图设置为偏左/中，添加相应位置，大小。(注:如果不设置，会导致标签使图形压缩)

![image-20210914230228550](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210914230228550.png)

## 二. 甘特图

![image-20210915105447917](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915105447917.png)

**(1).导入数据源**

![image-20210915105641050](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915105641050.png)

**(2).拖拽字段**

1.将【实际开始日期】拖到列这一栏，并将其设置为度量的**日**。

2.将【阶段】，【项目名称】拖到行这一栏。将【实际用天】拖到大小这一栏（如何没有这个度量值），可通过创建计算字段来计算。

![image-20210915122358843](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915122358843-16438177583414.png)

**(3).添加参考线/区间**

1.分别将【实际开始日期】，【实际完成日期】，【计划开始日期】，【计划完成日期】拖到标记下的**详细信息**，并将其全部设置为度量的**日**。

2.添加参考线，设置如下

![image-20210915123240683](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915123240683.png)

3.也可添加参考区间。

![image-20210915123338403](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915123338403.png)

**(4).图表变色**

接下来可以按照具体要求制作

1.如果想要图表显示出负责人，可之间将【负责人】拖到颜色

![image-20210915123514454](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915123514454.png)

2.如果想要图表表示出完成情况而显示相应的颜色

可创建计算字段，并将其拖到颜色。

![image-20210915123616659](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915123616659.png)

![image-20210915123711494](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915123711494.png)

## 三. 瀑布图

![image-20210915124550724](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915124550724.png)

**(1)导入数据源**

示例超市

![image-20210915124740521](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915124740521.png)

**(2)字段拖拽**

将【利润】拖到行这一栏上，【子类别】拖到列这一栏上，按利润从小到大排列，并将标记下的自动改成甘特条形图。

![image-20210915222209511](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915222209511.png)

**(3)汇总指标**

将【利润】快速表计算——汇总

![image-20210915222433974](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915222433974.png)

**(4)创建计算字段**

为了得到直条的长度，这里计算负值的【利润】值，并将其拖到大小

![image-20210915222635710](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915222635710.png)

![image-20210915223207240](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915223207240.png)

**(5)添加标签/色彩**

![image-20210915223321229](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915223321229.png)

**(6)添加行总计**

![image-20210915223530245](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210915223530245.png)

## 四. 镶边面积图

![image-20211004091328405](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004091328405.png)

**(1)导入数据源**

示例超市

![image-20210926104231413](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926104231413.png)

**(2)拖拽字段**

将【订单日期】拖拽到列这一栏。，【销售额】拖拽到列这一栏。【类别】拖拽到标记下的颜色。

![image-20210926104344827](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926104344827.png)

**(3)创建计算字段**

销售额\_办公用品

![image-20210926105109708](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926105109708.png)

销售额\_家具

![image-20210926105139658](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926105139658.png)

销售额\_技术

![image-20211004090235497](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004090235497.png)

**(4)合并字段**

将【销售额\_办公用品]拖到行这一栏，【销售额】的后面

将标记下的 总和【销售额\_办公用品】中的类别去掉

![image-20210926110241556](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926110241556.png)

将【销售额\_家具】拖到销售额\_办公用品图的前面

![image-20210926110603530](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926110603530.png)

将【销售额\_技术】拖到标记下的度量值中

![image-20211004090512232](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004090512232.png)

(5)调节顺序和标记

![image-20211004090801864](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004090801864.png)

对应顺序就是面积图的顺序

![image-20211004090853081](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004090853081.png)

**(6)更改公式**

将标记下的总和（销售额\_技术）的公式更改为

**SUM([销售额_技术])+SUM([销售额_家具])**

将标记下的总和（销售额\_办公用品）的公式更改为

**SUM([销售额_办公用品])+SUM([销售额_技术])+SUM([销售额_家具])**

之后双轴，再同步轴。

![image-20211004091235657](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20211004091235657.png)

最后按自己需求更改标签颜色这些

## 五. 阴影坡度图

![image-20210926110031273](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926110031273.png)

**(1)导入数据源**

示例超市

![image-20210926104231413](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926104231413-164379206449122.png)

**(2)拖拽字段**

将【订单日期】拖拽到列这一栏。，【销售额】拖拽到列这一栏。【类别】拖拽到标记下的颜色。

![image-20210926104344827](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926104344827-164379214759035.png)

**(3)创建计算字段**

销售额\_办公用品

![image-20210926105109708](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926105109708-164379214594433.png)

销售额\_家具

![image-20210926105139658](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926105139658-164379214402431.png)

**(4)合并字段**

将【销售额\_办公用品]拖到行这一栏，【销售额】的后面

将标记下的 总和【销售额\_办公用品】中的类别去掉

![image-20210926110241556](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926110241556-164379214166129.png)

将【销售额\_家具】拖到销售额\_办公用品图的前面

![image-20210926110603530](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926110603530-164379213992227.png)

之后将标记下的度量值改成区域，调整总和（销售额\_办公用品）与总和（销售额\_家具的位置。

![image-20210926110946050](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926110946050.png)

**(5)更改公式**

将标记下的总和（销售额\_家具）的公式更改为

**SUM([销售额_家具])-SUM([销售额_办公用品])**

之后双轴，再同步轴。

![image-20210926111358123](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926111358123.png)

**(6)更改颜色**

将销售额\_办公用品更改为白色

![image-20210926112217580](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/draw/image-20210926112217580.png)

最后再自由调整即可
