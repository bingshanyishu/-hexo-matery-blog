---
title: Tableau绘制K线图、布林线、圆环图、雷达图
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
abbrlink: 220203ab
date: 2022-02-03 00:38:48
summary:
img:
password:
---

# Tableau 绘制 K 线图、布林线、圆环图、雷达图

## 一. K 线图

![image-20211004105719192](https://img-blog.csdnimg.cn/img_convert/e5ded413b7fca9ace07384e54adf666e.png)

### 1.1 导入数据源

![image-20211004093731975](https://img-blog.csdnimg.cn/img_convert/86be140f92702b67eef51d81ca741a81.png)

### 1.2 拖拽字段

将【日期】托到列这一栏，并将其改为年/月/日类型

![image-20211004094127869](https://img-blog.csdnimg.cn/img_convert/c5e5407832ca7c617045ad202841ed03.png)

将【最低】拖到行这一栏。将【日期】拖到筛选，筛选字段设置为**日期范围**，日期大体设置为 2020/6/11~~2010/9/7（参考范围，可自己设置）

![image-20211004100428576](https://img-blog.csdnimg.cn/img_convert/36186f506f2be69ac2965243d5a6fe7e.png)

### 1.3 创建计算字段

创建计算字段，名字为**高低差**，公式为**[最高]-[最低]**，创建之后将其拖到标记下的**大小**，并将将其改成**甘特条形图**

![image-20211004102047269](https://img-blog.csdnimg.cn/img_convert/51052d0d1867d68ff9bbb912a613d031.png)

### 1.4 编辑轴

分别将【开盘】，【收盘】拖到**详细信息**，之后编辑轴，设定范围从**2300 到 2800**

![image-20211004101724808](https://img-blog.csdnimg.cn/img_convert/4658767a4f13c409fd34e6a479853de6.png)

### 1.5 做双图

创建计算字段，将其命名为**收开盘价差**，公式为**[收盘]-[开盘]**

![image-20211004101955928](https://img-blog.csdnimg.cn/img_convert/5f4afee54fa71025314f9091fbe0a877.png)

将【开盘】拖到行这一栏，将【收开盘价差】拖到标记下**总和（开盘）**的**大小**标记下

![image-20211004102454517](https://img-blog.csdnimg.cn/img_convert/b1b5e9a50f4f22c0ceb2d915aa90d8cb.png)

之后**双轴、同步轴**

![image-20211004104126831](https://img-blog.csdnimg.cn/img_convert/2431ba6f181fd42228a1478bb26d14b0.png)

### 1.6 修改颜色（涨跌）

将**总和（最低）**的大小减小，之后创建计算字段，

![image-20211004104444106](https://img-blog.csdnimg.cn/img_convert/da5640abf18ca259e70f3b1731fd7b96.png)

名字为**涨跌情况**，公式为**IIF([收盘]>[开盘],'涨','跌')**，将其拖拽到**总和（开盘）**下的颜色标记中，并按要求设置颜色，，这里将跌设置为红色，涨设置为蓝色。

![image-20211004104718805](https://img-blog.csdnimg.cn/img_convert/9578976cab8e5633383272151b012a4f.png)

最后调整对应坐标轴，标题这些即可

![image-20211004105112673](https://img-blog.csdnimg.cn/img_convert/b3812e7c03b885585c1e0ee3021e6656.png)

## 二. 布林线

![image-20211004125116885](https://img-blog.csdnimg.cn/img_convert/d3c1e9d3d046c9ce634e6a8242e661fc.png)

### 2.1 导入数据源

![image-20211004110025776](https://img-blog.csdnimg.cn/img_convert/46d567ac2a190aeb5e1dfd00a3a495a4.png)

### 2.2 拖拽字段

将【日期】拖拽到列这一栏，将其格式设置为**天**，将【收盘】拖拽到行这一栏，将其度量设置为平均值。将【日期】拖拽到筛选器中，设定筛选范围为**2019/5/25~~2020/9/7**..

![image-20211004110759168](https://img-blog.csdnimg.cn/img_convert/dda9e4ba91ca1ed1dce7e3656fc30b8c.png)

修改坐标轴范围为最小**2000**

![image-20211004111948071](https://img-blog.csdnimg.cn/img_convert/b533afa1005b95f82e283ac1881b560f.png)

### 2.3 创建参数

鼠标右键 创建参数 参数名字为移动窗口，数据类型设置为整数，允许的值改为范围，，值范围改为最小值：1，最大值：30，步长：1，，之后**显示参数控件**

![image-20211004111534911](https://img-blog.csdnimg.cn/img_convert/116e2538d88bf1a119255aa5a27931bb.png)

### 2.4 快速表计算

将行上的平均值（收盘）进行**移动平均**的快速表计算，将其拖到**数据-度量**中并进行编辑，

修改名字为**MA**，将其公式中的**-2 改为-移动窗口**

![image-20211004113240901](https://img-blog.csdnimg.cn/img_convert/bf9eb21db7f53d6679ff1e0f4062b0c8.png)

之后将 MA 替换原来的平均值（收盘），再将【收盘】将其拖到坐标轴中 。并重新设置坐标轴范围

![image-20211004113349796](https://img-blog.csdnimg.cn/img_convert/7f7bedb1b0142a5600c8d5ef49287652.png)

![image-20211004122241979](https://img-blog.csdnimg.cn/img_convert/7be32d780a99d851a1f953975f10b9ec.png)

### 2.5 创建 SD 计算字段与参数

创建计算字段，名字为 SD，公式为**WINDOW_STDEV(AVG([收盘]),-移动窗口,0)**

![image-20211004122607550](https://img-blog.csdnimg.cn/img_convert/75928671ffc53077dd5cad37ae1f6779.png)

创建参数，名字为 SD 倍数，，数据类型为浮点，当前值为 1，显示格式设置为一位小数，允许的值为范围，最小值为 1，最大值为 3.。最后创建完毕后显示参数控件。

![image-20211004122840399](https://img-blog.csdnimg.cn/img_convert/38f86e72f999e98fb339b15a8c6bdae2.png)

### 2.6 创建上轨与下轨

创建计算字段，名字为 UP，公式为[MA]+[SD 倍数]\*[SD]

创建计算字段，名字为 DOWN，公式为[MA]-[SD 倍数]\*[SD]

![image-20211004123344081](https://img-blog.csdnimg.cn/img_convert/16820722c0f91065be9f924bc9594d3b.png)

### 2.7 添加报警设定

将度量值下的【收盘】度量改成平均值，拖到最右边，再同步轴，然后去掉这个轴

![image-20211004123651926](https://img-blog.csdnimg.cn/img_convert/f94b5f4de1aeddd1301fa99b15497cd4.png)

创建计算字段

名字为**是否报警**

公式为：**IIF(AVG([收盘])<UP AND AVG([收盘])>[DOWN],FALSE,TRUE)**

![image-20211004124106084](https://img-blog.csdnimg.cn/img_convert/3c8c16c6b408f1b1afd19d159b7bdf37.png)

将其拖到标记中的**平均值（收盘）**中的颜色里，，调节颜色与不透明度，，将**平均值（收盘）**的不透明度设置为 100%，将度量值的颜色设置为 50%，再更改各线的颜色，增加美观与辨别度

![image-20211004124738566](https://img-blog.csdnimg.cn/img_convert/5ccff068baa41d71598548cb464f6158.png)

## 三. 圆环图

![image-20211004135308267](https://img-blog.csdnimg.cn/img_convert/20922c8908d05d4c41a535f1d78e8e29.png)

有的版本没有记录数这个字段，这里提供了两种绘制方法，不过思路是一样的。

### 3.1 导入数据源

示例超市

![image-20211004125459893](https://img-blog.csdnimg.cn/img_convert/929995817d90946f45732e1b2442c5a8.png)

### 3.2 步骤（有记录数）

#### 3.2.1 创建饼图

将【类别】拖到标记下的颜色中，将其改成**饼图**，将记录数拖拽到标记下的**角度**（要改成饼图后才有）

![image-20211004133705060](https://img-blog.csdnimg.cn/img_convert/da401a6423174b33beafe5d9bd5d16d7.png)

#### 3.3.2 创建双图

将【记录数】拖拽到行这一栏，并再复制一个，将两个【记录数】的度量改成最小值。移除第二个图的类别标记

![image-20211004134230196](https://img-blog.csdnimg.cn/img_convert/ea2d39d101ea6c46aa208f61bf83168b.png)

#### 3.2.3 修改大小

将两个图，双轴，再同步轴

将视图改成**整个视图**，将标记下的**最小（记录数）**大小调大，标记下的**最小（记录数）（2）**大小稍微小点，并将其颜色改成**白色**

![image-20211004134649488](https://img-blog.csdnimg.cn/img_convert/84437a32f82c00bc6ffe50e15f63a3cb.png)

#### 3.2.4 添加标签

将【类别】、【记录数】拖到标记下的**最小（记录数）**的标签中，调节字体，字号大小

将【记录数】拖到标记下的**最小（记录数）**的标签中，调节字体，字号大小，标签再加**总数**

![image-20211004135244360](https://img-blog.csdnimg.cn/img_convert/b09fe33782b669119a8c7b1e734886c6.png)

## 3.3 步骤（无记录数）

### 3.3.1 创建饼图

将【类别】拖到标记下的颜色中，将其改成**饼图**，将类别拖拽到标记下的**角度**（要改成饼图后才有），将其度量改成计数

![image-20211004135425514](https://img-blog.csdnimg.cn/img_convert/a880f9ac2f2ba5ee1c3bec90207fb030.png)

### 3.3.2 创建双图

将【类别】拖拽到行这一栏，并再复制一个，将两个【类别】的度量改成计数。对两者进行快速表计算——排序

移除第二个图的类别标记

### 3.3.3 其余操作类似

## 四. 雷达图

![image-20211004165333756](https://img-blog.csdnimg.cn/img_convert/f917154c419c39e63bf37fb5658d1b95.png)

### 4.1 导入数据源

![image-20211004153428151](https://img-blog.csdnimg.cn/img_convert/7e058443c6605fe578b5f5df550bde93.png)

转置后更改名称

![image-20211004153703915](https://img-blog.csdnimg.cn/img_convert/db939f22fb872998d3798ae684e80c4c.png)

![image-20211004153829515](https://img-blog.csdnimg.cn/img_convert/d9474503146c463545ab29d9a97db399.png)

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

![image-20211004162139852](https://img-blog.csdnimg.cn/img_convert/42c49290358f7a3f2c93703525402c19.png)

（2）创建计算字段，

名字为**角度**

公式为：

```
IF [路径]=9 THEN 0
ELSE -([路径]-1)*2*PI()/8
END
```

![image-20211004162317467](https://img-blog.csdnimg.cn/img_convert/321e7d73dc2e6372899f814150954df5.png)

(3)创建计算字段

名字分别为 X,Y

X：公式：`[大小]*COS([角度])`

Y：公式：`[大小]*SIN([角度])`

![image-20211004162600867](https://img-blog.csdnimg.cn/img_convert/fead6cc2ce0e1607d88324901cfce4ad.png)

### 4.3 拖拽字段

将 X 拖拽到列这一栏，Y 拖拽到行这一栏，将 F1 拖拽到标记下的颜色中，将其类型有**自动**改成**线**，将【路径】拖拽到标记下的**路径**，，最后将取消聚合度量（菜单栏中的**分析**--->**聚合度量取消打勾**）

![image-20211004162935587](https://img-blog.csdnimg.cn/img_convert/17d2a37748d728525f72b72ba0b86ed0.png)

这时基本雏形就出来了

![image-20211004163328185](https://img-blog.csdnimg.cn/img_convert/2ee9b299c3062a0881eff6ba2d88a148.png)

### 4.4 添加标签

为了使标签位于最外层，可直接在外层点手动加，但显得很 LOW，这里才有创建计算字段来生成。

（1）创建计算字段

名字为性质标签

公式为：`if [大小]=5 THEN [性质] END`

![image-20211004163547459](https://img-blog.csdnimg.cn/img_convert/44f374cd1376c6e1e9c9fb3e8a6019bd.png)

（2）创建计算字段

名字为数据标签

公式为：

`CASE [F1]`
`WHEN '产品A' THEN [大小]`
`WHEN '产品B' THEN [大小]`
`WHEN '产品C' THEN [大小]`
`END`

![image-20211004163709423](https://img-blog.csdnimg.cn/img_convert/6744abac6d1aaf797a36a3396bca3080.png)

（3）拖拽标签

复制行上的 Y，创建双图

将【性质标签】拖拽到标记下的总和(Y)(2)中的标签中

将【数据标签】拖拽到标记下的总和(Y)中的标签中，将数据标签类型改成**离散**，点击标签，勾选**允许标签覆盖其他标记**复选框

![image-20211004164603884](https://img-blog.csdnimg.cn/img_convert/a8d1dc0c918ca6fb77a3b3648a0cbfe8.png)

### 4.5 去除坐标轴

将坐标轴去掉，也可添加筛选器来筛选产品，以方便观看。

![image-20211004165017295](https://img-blog.csdnimg.cn/img_convert/721bcf664483ecf51fc0875da8230cf5.png)

### 4.6 调整多余数据，颜色

将**易抽取性**中多余的数据隐藏掉（点击多余的数据，鼠标右键，将**标记标签改成从不显示**），将 5 个外围圆的颜色设置为灰色。

![image-20211004164530985](https://img-blog.csdnimg.cn/img_convert/779381218be620faabd941141056dd48.png)
