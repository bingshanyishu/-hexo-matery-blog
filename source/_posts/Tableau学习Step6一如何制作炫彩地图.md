---
title: Tableau学习Step6一如何制作炫彩地图
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
abbrlink: 220202af
date: 2022-02-02 22:08:59
summary: 
img:
password:
---



# Tableau学习Step6——如何制作炫彩地图

## 一.统计地图概述

![image-20210910173045599](https://img-blog.csdnimg.cn/img_convert/0334cd7ba852a4728eaf38ecadb0b048.png)

### 1.1 统计地图的基本概念

![image-20220111113405011](https://img-blog.csdnimg.cn/img_convert/28d7cb502e6db1c5a8d9a0cfcebe5a68.png)



- 统计地图的本质:数据的正确对应
    - 将数据信息和地理位置严格对应起来,并加以图形呈现
- 如何将数据和地理位置对应起来?
    - 将数据信息和其所在的地理点/地理区域直接关联起来
    - 将相应信息用适当的图形元素在相应地理点/地理区域加以表示
- 常见的数据对应方式
    - ·统计数据和地图数据分表/库存储,用地名关键字将两个数据表进行连接
    - ·当使用可识别的标准地名关键字时, Tableau中这种连接操作是自动进行的
        - ·例:“中国”、“ China”均可识别,但“三哥”、“巴铁”就会让 Tableau-脸懵圈



### 1.2 地图地图的优劣

合理运用地图展现数据关系和大小。

同样是展示总销售额和总订单数

![image-20220111113623180](https://img-blog.csdnimg.cn/img_convert/8055b65f15454c6b6ff367895d8dac46.png)





## 二.标准统计地图的绘制

![image-20210910173128549](https://img-blog.csdnimg.cn/img_convert/076a8fc18239763f3f79f7217d57313d.png)

### 2.1 比例符号地图

![image-20220111113750939](https://img-blog.csdnimg.cn/img_convert/6f8448fa97d3c5ad504758549a605f77.png)



![image-20220111115235129](https://img-blog.csdnimg.cn/img_convert/fa01ea9ae4699635b11a5d28b4ea37ca.png)





### 2.2 填充地图

![image-20220111115303051](https://img-blog.csdnimg.cn/img_convert/9761bcfdc2f6b5f63e9d4837022e0c62.png)

![image-20220111114143079](https://img-blog.csdnimg.cn/f282a5f3a9de4fa2a7b566afb651cdf6.png)





### 2.3 点分布图

![image-20220111115325660](https://img-blog.csdnimg.cn/img_convert/06052411f46951be92628eaaae9b832c.png)







### 2.4 热力图

![image-20220111115346068](https://img-blog.csdnimg.cn/img_convert/96df8d3ca3a42de08c8c6300f1b39ce3.png)





### 2.5 蜘蛛图

![image-20220111115435297](https://img-blog.csdnimg.cn/img_convert/a352a0fe3882eb484e3099906d442557.png)







### 2.6 动态路径图

![image-20220111115501192](https://img-blog.csdnimg.cn/img_convert/cbbfa69aee549d339035f9d91837cfb7.png)



### 2.7 复合统计地图

将统计地图与其他统计图层相叠加

- 统计地图显示主要信息
- 其他统计图显示主要信息二
    - 最常用的为饼图,其余图形种类非常少见
- 绘制要点
    - 以双轴图的方式进行图层的叠加
    - ·进行图层的配色调整,使关键信息更加突出



### 2.8 地图的编辑和设定

- 搜索框、界面操作钮等的使用
    - 显示比例尺
- 图形背景的深浅设置
    - 冲蚀效果
- 图层和数据层
    - 图层可供用户进行效果微调
    - ·数据层目前基本上是提供美国范围的数据





## 三.突破默认的地图框架

![image-20220111115924195](https://img-blog.csdnimg.cn/img_convert/6bf3209eaa6f79b7537d485b307eb131.png)



### 3.1 默认无法满足要求

![image-20210910215615884](https://img-blog.csdnimg.cn/img_convert/7c003e90ea88471b5fc45e1d556211bd.png)





### 3.2 如何处理非标准名称

![image-20210910220642518](https://img-blog.csdnimg.cn/img_convert/de47081a3d4fd95c4d18bfc10c859a11.png)



### 3.3 自定义地理信息数据

![image-20210910221321146](https://img-blog.csdnimg.cn/img_convert/2324915b7510b5b975d0bea316545e44.png)

### 3.4 基于已有地图添加新层级

![image-20220111115830032](https://img-blog.csdnimg.cn/img_convert/eae42c542598755fe4ae81448d2f7da7.png)

1

### 3.5 基于已有地理单元添加新的地理分层

![image-20220111130147103](https://img-blog.csdnimg.cn/img_convert/cdb8b019bfd6e74ceb6cf714a069a7c4.png)

![image-20210911102527099](https://img-blog.csdnimg.cn/img_convert/4e3d55c3ff93b8779752d7184589a5c2.png)





### 3.6 使用嵌套地图自动显示省市详情

![](https://img-blog.csdnimg.cn/0008d95196d345559ff0e68bed6911fc.png)





### 3.7 如何计算两点间的距离


数据格式整理

要求经纬度已在数据集中显式存在
以内连接方式关联两两数据点(并去除无意义的同点关联)

将原数据源中的数据取**并集**，连接方式为**<>**

![image-20220111132524419](https://img-blog.csdnimg.cn/img_convert/9183a5bbf1d0f6121bbdb05df377c0a2.png)



**在数据源中计算出两两点间距离**
用大圆距离公式计算实际距离(使用地球的平均半径)

创建计算字段：**距离**，将**距离变量设置为维度**,公式如下：

```
3959* ACOS( SIN(RADIANS([lat]))*SIN(RADIANS([lat2]))+
COS(RADIANS([lat]))*COS(RADIANS([lat2]))*
COS(RADIANS([long2])-RADIANS([long])))
```

![image-20220111134324029](https://img-blog.csdnimg.cn/img_convert/cb67fcda3368691df46f2089395eb411.png)





**在地图中显示出两两点间距离**
并设定为线标记下的颜色，修改标签显示至合适方式

将距离添加到**标签**，同时设置标签的只显示距离

![image-20220111134603369](https://img-blog.csdnimg.cn/img_convert/5cb2816a07ff5729b2e18eea2c376b74.png)

双轴，将国际名称添加到标签，合并双轴

![image-20220111134705963](https://img-blog.csdnimg.cn/img_convert/39ed8ba4c4f01fd9e3a0f30c1213486e.png)

为了更好交互，还可将**国际名称（直辖市名称1）拖到工具提示**，其设置如下

![image-20220111135136469](https://img-blog.csdnimg.cn/img_convert/3b3443258b9604dfa116dc4c5aa1a82e.png)







## 四.炫彩地图DIY

![image-20210910173235507](https://img-blog.csdnimg.cn/img_convert/9b36199f5e17317b6b64083d3a357555.png)





### 4.1 使用静态背景图片

- 截取符合需求的图源为静态图片
    - 谷歌地图
    - Open Street开源地图
- 测量四个端点的GPS坐标,以取得相应的横纵轴尺度范围
- 设定相应图片为地图的背景图像,设定纵横轴相对应的变量,以及变量的取值范围
- 取消背景地图的显示
- 根据显示效果调整纵横轴尺度,以使数据和背景地图准确匹配

![image-20210911132238298](https://img-blog.csdnimg.cn/img_convert/cb54381d3b28e1c94da2a82897e29aef.png)

（1）截取背景图片

![image-20220111135513418](https://img-blog.csdnimg.cn/img_convert/07f8ba0f4a094164b58af871e1a17e43.png)

（2）取左上角与右下角经纬度坐标

![image-20210911132100325](https://img-blog.csdnimg.cn/img_convert/34f07a03d0853b772f1c178c2345b17f.png)

（3）载入图片

![image-20210911131958349](https://img-blog.csdnimg.cn/img_convert/e92687f66d863160797c632cf3e97822.png)

![image-20210911132109193](https://img-blog.csdnimg.cn/img_convert/663699a0d14e6ce221f2142b7f4fdc5b.png)





### 4.2 使用自定义图片

方法同4.1，不断调试

![image-20220111135532519](https://img-blog.csdnimg.cn/img_convert/cc169da0744b202ae86fff41ada45c30.png)





### 4.3 绘制多边形地图与如何采集

- 采集封闭多边形各个连续端点的经纬度坐标
    - 同时记录各连续端点的绘制顺序
- 如果同一区域被分为多个独立多边形,则分别绘制,并取相同名称/D号即可
    - 为便于管理,应当为每个区域提供不同的subd
- 将经度、纬度变量指定为正确的地理角色
- 要求绘制多边形图形,并将绘制顺序变量设定为路径
    - 名称D变量用于区分不同地理区域, subid则辅助绘制不同的区域
- 推荐在线工具
    - https://drawingtool.powertoolsfortableau.com
    - https://tableaudraw.com/



### 4.使用外部地理空间文件

![image-20210911154426641](https://img-blog.csdnimg.cn/img_convert/ed3bcbf454c661885b2ad597d361e0b8.png)

### 5.使用在线地图服务

![image-20210911154959763](https://img-blog.csdnimg.cn/img_convert/5c1673c5973032673955c8152f61f1fa.png)
