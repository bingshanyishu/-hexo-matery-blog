---
title: Tableau绘制漏斗图、甘特图、瀑布图、镶边面积图、阴影坡度图
author: Breezs
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

![image-20210915105147655](https://img-blog.csdnimg.cn/img_convert/c065045c7b65c88bedb30d4cd4827a46.png)

**数据源**

![image-20220202163137490](https://img-blog.csdnimg.cn/img_convert/33df883ca7d1525a9beac8387dd5fc42.png)

### 1.1 分色直条漏斗图

（1）导入数据

（2）将【数量】拖到行这一栏，将【阶段】拖到标记下的颜色选项卡吗，之后对数量进行降序排列。![image-20210914204947551](https://img-blog.csdnimg.cn/img_convert/b973f92bd02e481446c8fa82358b8c9d.png)

（3)把【数量】拖到标记下的大小选项卡，**视图**设置为**整个视图**

![image-20210914205145965](https://img-blog.csdnimg.cn/img_convert/d7fd25e2633b46ad1f6ee9aaaaf4c200.png)

（4）把【阶段】，【数量】拖到标签选项卡，并对数量进行快速表计算——合计百分比。

![image-20210914205550841](https://img-blog.csdnimg.cn/img_convert/44da57f535b8315cea47f682b89e3f61.png)

（5）下面的图形由于太少而导致无法显示标签，对此可手动的选择，添加注释。（当然，为了美观，也可以选择不加）

![image-20210914205943824](https://img-blog.csdnimg.cn/img_convert/7ae03e2174b879ec4ac7ceb79b1fdc4e.png)

### 1.2 同色斜边框漏斗图

（1）导入数据

（2）将【数量】拖到行这一栏，将【阶段】拖到标记下的颜色选项卡吗，之后对数量进行降序排列。并将“标记”下的**自动**改为**区域**

![image-20210914210440979](https://img-blog.csdnimg.cn/img_convert/8cf50b62e32c361791b3facc48b51cbf.png)

（3）重复列一栏的【数量】，并将左边图的坐标轴倒序

![image-20210914210640460](https://img-blog.csdnimg.cn/img_convert/04a9d48d1d1f68da8dcaeaf68b7c07b7.png)

（4）将图表颜色不透明度改成 100%，鼠标右键设置格式，将边界的列分隔符改成无

![image-20210914210934112](https://img-blog.csdnimg.cn/img_convert/84c57c9bfb4b7a12044707f1b9b26eb6.png)

（5）去掉坐标轴，并为图表添加标签，左侧添加【阶段】，右侧添加【数量】的百分比。并调整相应得大小，位置。

![image-20210914222922042](https://img-blog.csdnimg.cn/img_convert/929ea322254ad120e7bc5f40049d33fe.png)

### 1.3 分条彩色漏斗图

（1）导入数据

（2）将【数量】拖到行这一栏，将【阶段】拖到标记下的颜色选项卡吗，之后对数量进行降序排列。把【阶段】拖到标记下得**颜色**。

![image-20210914223428455](https://img-blog.csdnimg.cn/img_convert/11c098b59bc5e765f32d886a5eb3c55c.png)

（3）复制【数量】这一栏，将【数量 2】标记下的自动改为**线**，【数量 1】标记下的自动改为**条形图**，并合并**双轴**，再**同步轴**

![image-20210914223930082](https://img-blog.csdnimg.cn/img_convert/9e37b69a6f51562505f4464c1d5ff757.png)

（4）同理，再做一个相同的图形

![image-20210914224058654](https://img-blog.csdnimg.cn/img_convert/7a34a3210d06e6c0193c917cd7a41b40.png)

（5)将第一个图形的轴倒序，并对图形鼠标右键——设置格式，将边界下的列分隔符改成无（以去掉合并图形中间的线），之后再去掉图形的坐标轴。

![image-20210914224429986](https://img-blog.csdnimg.cn/img_convert/0962e53dc8da028b60feebc2505a11c1.png)

（6）将【阶段】拖到【数量 2】的标记下的**标签**中，【数量】拖到【数量 4】的标记下的**标签**中。并快速表计算——**合计百分比**。调整相应的大小，位置。

![image-20210914225102945](https://img-blog.csdnimg.cn/img_convert/4e0bfd71593db62392fb4c17b0671dc4.png)

（7）如果不想要边缘的线，也可以删除两个线图所对应栏的【数量】，然后添加标签，并将此时标签左侧图设置为偏右/中，右侧图设置为偏左/中，添加相应位置，大小。(注:如果不设置，会导致标签使图形压缩)

![image-20210914230228550](https://img-blog.csdnimg.cn/img_convert/b5b88f091d5dda3904995086076092ff.png)

## 二. 甘特图

![image-20210915105447917](https://img-blog.csdnimg.cn/img_convert/214acd928a12328a383ef1304e12e697.png)

**(1).导入数据源**

![image-20210915105641050](https://img-blog.csdnimg.cn/img_convert/c419d8faeb7f6c9b913fa4af156645f8.png)

**(2).拖拽字段**

1.将【实际开始日期】拖到列这一栏，并将其设置为度量的**日**。

2.将【阶段】，【项目名称】拖到行这一栏。将【实际用天】拖到大小这一栏（如何没有这个度量值），可通过创建计算字段来计算。

![image-20210915122358843](https://img-blog.csdnimg.cn/img_convert/bb78b881416eb21e7df97385794e7231.png)

**(3).添加参考线/区间**

1.分别将【实际开始日期】，【实际完成日期】，【计划开始日期】，【计划完成日期】拖到标记下的**详细信息**，并将其全部设置为度量的**日**。

2.添加参考线，设置如下

![image-20210915123240683](https://img-blog.csdnimg.cn/img_convert/d925a6c8a3b21371695e0cdc99a179a3.png)

3.也可添加参考区间。

![image-20210915123338403](https://img-blog.csdnimg.cn/img_convert/81ef925548772ccffa44b90900be1eb0.png)

**(4).图表变色**

接下来可以按照具体要求制作

1.如果想要图表显示出负责人，可之间将【负责人】拖到颜色

![image-20210915123514454](https://img-blog.csdnimg.cn/img_convert/80c4adafd2a27279947ffae60fadce49.png)

2.如果想要图表表示出完成情况而显示相应的颜色

可创建计算字段，并将其拖到颜色。

![image-20210915123616659](https://img-blog.csdnimg.cn/img_convert/cebe9bbed065a95884a63b9aa28cdcf2.png)

![image-20210915123711494](https://img-blog.csdnimg.cn/img_convert/d268555a0c415309c7baa04df8b8830e.png)

## 三. 瀑布图

![image-20210915124550724](https://img-blog.csdnimg.cn/img_convert/cf1f732b84aa5cbf3771aa2a424c959b.png)

**(1)导入数据源**

示例超市

![image-20210915124740521](https://img-blog.csdnimg.cn/img_convert/b47fe3b7906c9394706de0007687a623.png)

**(2)字段拖拽**

将【利润】拖到行这一栏上，【子类别】拖到列这一栏上，按利润从小到大排列，并将标记下的自动改成甘特条形图。

![image-20210915222209511](https://img-blog.csdnimg.cn/img_convert/43d8d5b24df6a15e2de2115a70589eeb.png)

**(3)汇总指标**

将【利润】快速表计算——汇总

![image-20210915222433974](https://img-blog.csdnimg.cn/img_convert/9c5d6a3236f265ab1e630dfd387ff456.png)

**(4)创建计算字段**

为了得到直条的长度，这里计算负值的【利润】值，并将其拖到大小

![image-20210915222635710](https://img-blog.csdnimg.cn/img_convert/bb22808bbdbf6ae74e46e312197d7d33.png)

![image-20210915223207240](https://img-blog.csdnimg.cn/img_convert/088e135f2ef03e87d2266dc313c04168.png)

**(5)添加标签/色彩**

![image-20210915223321229](https://img-blog.csdnimg.cn/img_convert/044aeaa2e278db54f279fa854d4491b0.png)

**(6)添加行总计**

![image-20210915223530245](https://img-blog.csdnimg.cn/img_convert/7197a8df624164a3cd284c59b1483041.png)

## 四. 镶边面积图

![image-20211004091328405](https://img-blog.csdnimg.cn/img_convert/365719775ea757490d204dc9fc9e6294.png)

**(1)导入数据源**

示例超市

![image-20210926104231413](https://img-blog.csdnimg.cn/img_convert/f3ba0342167363eb53c72d470e3766b5.png)

**(2)拖拽字段**

将【订单日期】拖拽到列这一栏。，【销售额】拖拽到列这一栏。【类别】拖拽到标记下的颜色。

![image-20210926104344827](https://img-blog.csdnimg.cn/img_convert/38c32a2e81310db51f98618d3fe0bdde.png)

**(3)创建计算字段**

销售额\_办公用品

![image-20210926105109708](https://img-blog.csdnimg.cn/img_convert/bdc4ff132bf363ff048b397833d019ab.png)

销售额\_家具

![image-20210926105139658](https://img-blog.csdnimg.cn/img_convert/101070a54b217ce7577f4c3a11932ff4.png)

销售额\_技术

![image-20211004090235497](https://img-blog.csdnimg.cn/img_convert/19eb581174462ee1ab75250be0ba41b0.png)

**(4)合并字段**

将【销售额\_办公用品]拖到行这一栏，【销售额】的后面

将标记下的 总和【销售额\_办公用品】中的类别去掉

![image-20210926110241556](https://img-blog.csdnimg.cn/img_convert/0687706142710e683df50944de4afc2f.png)

将【销售额\_家具】拖到销售额\_办公用品图的前面

![image-20210926110603530](https://img-blog.csdnimg.cn/img_convert/288445b1b2bb46f547f00500951deb9e.png)

将【销售额\_技术】拖到标记下的度量值中

![image-20211004090512232](https://img-blog.csdnimg.cn/img_convert/b68722f549ee50a55c9a4b5702fede01.png)

(5)调节顺序和标记

![image-20211004090801864](https://img-blog.csdnimg.cn/img_convert/1f0cabcaeb613b872b7b3b6b04ddcb80.png)

对应顺序就是面积图的顺序

![image-20211004090853081](https://img-blog.csdnimg.cn/img_convert/955aaf99b3580d3deaa8517a93554a0c.png)

**(6)更改公式**

将标记下的总和（销售额\_技术）的公式更改为

**SUM([销售额_技术])+SUM([销售额_家具])**

将标记下的总和（销售额\_办公用品）的公式更改为

**SUM([销售额_办公用品])+SUM([销售额_技术])+SUM([销售额_家具])**

之后双轴，再同步轴。

![image-20211004091235657](https://img-blog.csdnimg.cn/img_convert/3229099c21b7fa85f8d13e6c794785cf.png)

最后按自己需求更改标签颜色这些

## 五. 阴影坡度图

![image-20210926110031273](https://img-blog.csdnimg.cn/img_convert/91559c9341e7efbc6f3b0dd6f41df2f6.png)

**(1)导入数据源**

示例超市

![image-20210926104231413](https://img-blog.csdnimg.cn/img_convert/74ccfb0caabd6bb86ee3e2e00e4b7e2d.png)

**(2)拖拽字段**

将【订单日期】拖拽到列这一栏。，【销售额】拖拽到列这一栏。【类别】拖拽到标记下的颜色。

![image-20210926104344827](https://img-blog.csdnimg.cn/img_convert/b91892e3c216eb3bf740bccc9ceca0a7.png)

**(3)创建计算字段**

销售额\_办公用品

![image-20210926105109708](https://img-blog.csdnimg.cn/img_convert/8ea6cbebc1a042c76c71c77b7822a8d0.png)

销售额\_家具

![image-20210926105139658](https://img-blog.csdnimg.cn/img_convert/0a136b6f9c5c707107b56b83e8d9a74b.png)

**(4)合并字段**

将【销售额\_办公用品]拖到行这一栏，【销售额】的后面

将标记下的 总和【销售额\_办公用品】中的类别去掉

![image-20210926110241556](https://img-blog.csdnimg.cn/img_convert/397fe9417282e5dcc19a97b68b2810f7.png)

将【销售额\_家具】拖到销售额\_办公用品图的前面

![image-20210926110603530](https://img-blog.csdnimg.cn/img_convert/0965128915910626741c0a7025cb6fb5.png)

之后将标记下的度量值改成区域，调整总和（销售额\_办公用品）与总和（销售额\_家具的位置。

![image-20210926110946050](https://img-blog.csdnimg.cn/img_convert/481c7618d9c42207d6a2d5d98ad7489e.png)

**(5)更改公式**

将标记下的总和（销售额\_家具）的公式更改为

**SUM([销售额_家具])-SUM([销售额_办公用品])**

之后双轴，再同步轴。

![image-20210926111358123](https://img-blog.csdnimg.cn/img_convert/d1f3703cbc525cd4e87b7ead8f96f1d4.png)

**(6)更改颜色**

将销售额\_办公用品更改为白色

![image-20210926112217580](https://img-blog.csdnimg.cn/img_convert/7dae596f9fffb4cf0d77aab48cc6a05d.png)

最后再自由调整即可
