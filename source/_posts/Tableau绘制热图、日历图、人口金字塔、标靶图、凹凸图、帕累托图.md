---
title: Tableau绘制热图、日历图、人口金字塔、标靶图、凹凸图、帕累托图
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
abbrlink: 220202ba
date: 2022-02-03 00:13:48
summary: 本文就Tableau如何绘制热图、日历图、人口金字塔、标靶图、凹凸图、帕累托图等重点图形进行论述
img:
password:
---

# Tableau 绘图一热图、日历图、人口金字塔、标靶图、凹凸图、帕累托图

## 一.热图

![image-20210911164314869](https://img-blog.csdnimg.cn/img_convert/aa4099948b2dd3aa67e067cfa296a573.png)

**例子：示例超市**

![image-20210911213634687](https://img-blog.csdnimg.cn/img_convert/5b1eda1f300caf552408602b22fe3a3f.png)可以通过更改颜色来改变颜色的显示情况

## 二.日历/日历图

![image-20210911221412816](https://img-blog.csdnimg.cn/img_convert/0091605229c99fd9eed883fc873b6776.png)

数据源：示例超市

![image-20210911223231847](https://img-blog.csdnimg.cn/img_convert/97672e262e37fb506c76a384ff2bb9f2.png)

按要求修改日期的格式

## 三.人口金字塔/旋风图

![image-20220111150840162](https://img-blog.csdnimg.cn/img_convert/752982a804045f32d99c5d5acd9d128b.png)

数据源：绘图数据

由于数据源中含有 85 岁以上的人，不能之间判断。这里可将 Age 转换为字符串，然后创建计算字段，命名为

```
年龄=if [Age]='85+' THEN 85 ELSE INT([Age])
END
```

![image-20220111153416842](https://img-blog.csdnimg.cn/img_convert/9f2af62372265e25af57330775d64df5.png)

将**年龄**创建数据桶

![image-20220111153725596](https://img-blog.csdnimg.cn/img_convert/0b792e995044920602499a6ef83a49ae.png)

再分别创建以下字段

![image-20220111154017348](https://img-blog.csdnimg.cn/img_convert/35c883176cf6610afb7dd68a704761ea.png)

分别拖字段，以及倒序轴，设置颜色

![image-20220111165622853](https://img-blog.csdnimg.cn/img_convert/4a2d3e9c78739c72e2991d4de0b7d227.png)

## 四. 标靶图

![image-20210912215950728](https://img-blog.csdnimg.cn/img_convert/9699c5d150ce09fe9a9a29c56ecdd8a6.png)

### 4.1 数据源:示例超市+销售目标

从 Tableau【帮助】——【示例工作簿】——【示例超市】加载

### 4.2 步骤：

（1）新建一个工作簿

（2）把【销售额】拖到列这一栏，把【订单日期】拖到行这一栏，同时钻取日期为年和月，之后再把【细分】拖到行这一栏（为了图表美观，可【订单日期】拖到**筛选器**，筛选任意一年的时间，本图表筛选日期为**年——2016**，

![image-20210912221532086](https://img-blog.csdnimg.cn/img_convert/fdf850d2eb218480580e7b935d51be02.png)

（3）切换数据源为销售目标，把销售目标（注意：这里是度量值的销售目标，而非数据源名）

![image-20210912221729733](https://img-blog.csdnimg.cn/img_convert/53f3003310327a185860de89b8fa1491.png)

（4）为图添加趋势线，点击分析，将参考线拖到单元格，并把值改为【总和(销售目标)】

![image-20210912221958524](https://img-blog.csdnimg.cn/img_convert/73244e4a82cb7c14f7db5e8b8e43bf2a.png)

(5)切换到示例-超市数据源，将度量值【销售额是否超过目标？】拖入到**标记**中的**颜色**,此时图表按是否达到目标有不同的颜色，若没有该度量值，可按下列公式计算

![image-20210912222504824](https://img-blog.csdnimg.cn/img_convert/912c741e8351888567c5d0d4bd42f1ca.png)

![image-20210912222359589](https://img-blog.csdnimg.cn/img_convert/21add93942d9c9a9383cacc97ba5acfa.png)

（6）为了在与图表互动时能够显示差值，可把【销售额】拖入到**详细信息**，再把公式编辑成如下第一张图所示。之后点击工具提示，把内容改为如第二张图所示

![image-20210912223017469](https://img-blog.csdnimg.cn/img_convert/b4e4ef03214569a15f4bdc02f503e107.png)

![image-20210912223359812](https://img-blog.csdnimg.cn/img_convert/c689a529c0588e2717cdd4f4d9614287.png)

（7）点击**分析**，把**分布区间**拖入到弹出的窗口的**单元格**中，值可设为 40,60,80,填充选取一个颜色，，选择向下填充复选框。

![image-20210912223809345](https://img-blog.csdnimg.cn/img_convert/ffcc743dffb0700eb4c9a515b1cbe314.png)

（8）结果——（可按自己要求更改图表配色）

![image-20210912223940195](https://img-blog.csdnimg.cn/img_convert/a7a5b4c117922409c8105c41cc6a75bc.png)

## 五. 凹凸图

![image-20210913113257930](https://img-blog.csdnimg.cn/img_convert/0793cbbf86f9abb11804620a51bfe7fa.png)

### 5.1 数据源

系统自带示例超市

### 5.2 步骤

（1）打开示例超市数据源

（2）将【订单日期】拖到列这一栏，把【销售额】拖到行这一栏

把【子类别】托到标记中的**颜色**。

![image-20210913113908536](https://img-blog.csdnimg.cn/img_convert/2785d1385d1eb2bd5781acbb10ffa420.png)

（3）把【销售额】添加快速表计算，之后再编辑快速表计算，**计算依据**改为特定维度，只勾选【子类别】复选框，大致可以得到凹凸图雏形。

![image-20210913114058304](https://img-blog.csdnimg.cn/img_convert/e49a2b3c656eb41623ac54bd97fe1dfb.png)

![image-20210913114244066](https://img-blog.csdnimg.cn/img_convert/9ef19548bdd6442b565e7ea56921f7f1.png)

（4）按住 CTRL 键把销售额往后拖，即复制销售额这一栏，之后把第二个**总和（销售额）**改为**圆**，并点击**标签**，勾选**显示标记标签**和**允许标签覆盖其他标记**两个复选框,把对齐中的**水平与垂直**均设置为**居中**![image-20210913115428668](https://img-blog.csdnimg.cn/img_convert/fb4899144e4f218964b67991b98f8f5b.png)

（5)之后点击行这一栏的第二个【销售额】的小三角，然后弹出的对话框点击**双轴**，可得到基本图形了，但仍有不足，线与圆之间不对称，这是由于两个轴不同步引起的。此时可对**右侧坐标轴鼠标右键**，点击**同步轴**

![image-20210913115920574](https://img-blog.csdnimg.cn/img_convert/ce744205ba2bfacf4c4e43c96f9ee430.png)

![image-20210913120100145](https://img-blog.csdnimg.cn/img_convert/f7914003ea876b9c5a561e3a5cf2135c.png)

（6）**调整坐标刻度为倒序**，此时排序为 1 的排到最上面，之后由于坐标轴在凹凸图中没有意义，可把坐标轴隐藏掉。分别对两个轴鼠标右键，去掉**显示标题的勾**

![image-20210913120324077](https://img-blog.csdnimg.cn/img_convert/a590ad28da0e59e021d6b81215c6ffe7.png)

![image-20210913120457532](https://img-blog.csdnimg.cn/img_convert/3a33c73fb733dc7184c2cb8eb81c8dfb.png)

（7）结果

![image-20210913120722634](https://img-blog.csdnimg.cn/img_convert/976cf76362c9deb7bf9733a7da9f622b.png)

## 六. 帕累托图

![image-20210913221812167](https://img-blog.csdnimg.cn/img_convert/0172206085bb8b6ae6b57851f65efa97.png)

**数据源——示例超市**

### 6.1 基础版

（1）连接数据源，新建一个工作簿

（2）将【子类别】拖到列这一栏，将【销售额】拖到行这一栏，之后对【销售额】进行降序排序，即可得到基本的条形图

![image-20210913222419420](https://img-blog.csdnimg.cn/img_convert/d8c262a9d86117b8940ef842a5fbd6a7.png)

（3）将按住 CTRL 的同时把行上的【销售额】往后拖一个，即复制销售额，之后再对第二个销售额快速表计算——汇总

![image-20210913222822497](https://img-blog.csdnimg.cn/img_convert/448da8807a79cf685c3a00cf418a47de.png)

（4）将第二个【销售额】的标记改为**线**，，之后编辑表计算，在弹出来的对话框中计算依据勾选特定维度，最下面勾选添加辅助计算复选框，在新的辅助计算中**从属计算类型**选择**合计百分比**，**计算依据**改为**特定维度**![image-20210913223442577](https://img-blog.csdnimg.cn/img_convert/182bb01923a93718c4f049550172bc2e.png)

（5）合并双轴，并把第一个【销售额】的标记改为**条形图**

![image-20210913224123858](https://img-blog.csdnimg.cn/img_convert/3509155afa6e8e86cdbbec7527f04d67.png)

（6）可为图表添加常量线，便于决策，最后图表如果颜色不美观，还可更改图表颜色——点击**标记下的”全部“中的颜色**即可。

![image-20210913224409214](https://img-blog.csdnimg.cn/img_convert/5d90b9203107f51b76d8fefdfb7ee461.png)

### 6.2 复杂版

复杂版，即，将横坐标改为百分比递增，而不再是子类别

（1)在基础版的图形上进行更改，将【子类别】拖到标记下的全部的**详细信息**中，同时将列这一栏的**度量**改为**计数（不同）**

![image-20210913225254520](https://img-blog.csdnimg.cn/img_convert/db3040acde86c132179d1adbec805b37.png)

（2）对列这一栏的子类别进行添加表计算，主要计算类型改为**汇总**，计算依据改为**特定维度**，排序顺序改为**自定义排序**，选择【销售额】，**降序**排序，并勾选**添加辅助计算**复选框，从属计算类型改为**合计百分比**，计算依据改为**特定维度**

![image-20210913225709312](https://img-blog.csdnimg.cn/img_convert/6587f6961a66c0e4b0152fb3098867ff.png)

（3）也可为图表添加参考线

![image-20210913231545913](https://img-blog.csdnimg.cn/img_convert/cd710628a7d456583ff3b2c39cc518b1.png)

(4)结果

![image-20210913231622180](https://img-blog.csdnimg.cn/img_convert/f80a8348c91e3443aad6e9ed98faa5d1.png)
