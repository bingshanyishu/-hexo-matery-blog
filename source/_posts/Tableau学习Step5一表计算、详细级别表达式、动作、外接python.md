---
title: Tableau学习Step5一表计算、详细级别表达式、动作、外接python
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
abbrlink: 220202ae
date: 2022-02-02 22:07:59
summary: 表计算、详细级别表达式、动作、外接python,什么是表计算,是特殊类型的计算字段
img:
password:
---

# Tableau 学习 Step5 一表计算、详细级别表达式、动作、外接 python

## 一. 表计算

### 1.1 什么是表计算

-   是特殊类型的计算字段
-   根据当前的可视化内容（基于当前内容构建的虚拟表）进行计算，如排名、汇总、差分、定基比/环比.......
-   表计算并不考虑当前可视化内容中被筛选掉的任何度量或维度
-   表计算的结果并不影响数据源中的数据表

![image-20220111103908879](https://img-blog.csdnimg.cn/img_convert/a4c647aa75f877fe469c8561edc6f3f2.png)

### 1.2 分区与寻址

-   分区字段

    -   用于定义计算组方式(确定执行表计算所针对的数据范围)的维度
    -   分区字段将视图拆分成多个子视图(或子表),系统在每个分区内单独执行表计算

-   寻址字段

-   执行表计算所需要使用的其余维度
-   用于确定计算时的移动方向
    -   横穿(从左到右)
    -   向下(从上到下)
    -   横穿,然后向下
    -   向下,然后横穿

#### 1.2.1 横穿 VS 向下

![image-20220111103814918](https://img-blog.csdnimg.cn/img_convert/8f22cf3a93916ac0392ad2d53a501d76.png)

#### 1.2.2 横穿,然后向下 VS 向下,然后横穿

![image-20220111103940525](https://img-blog.csdnimg.cn/img_convert/7e31ee60cec0e438de4871439d4edaf5.png)

#### 1.2.3 加入分区维度

![image-20220111104012802](https://img-blog.csdnimg.cn/img_convert/6157872768ccf59948469c7c6447b0cd.png)

#### 1.2.4 单元格内计算与特殊级别

![image-20220111104040224](https://img-blog.csdnimg.cn/img_convert/fd02949a7408c15fbfec346b68e070f6.png)

### 1.3 表计算常见类型

![image-20220110212928540](https://img-blog.csdnimg.cn/img_convert/fbdb88cb3405982e8ba688e228ca0b76.png)

### 1.4 如何创建表计算

#### 1.4.1 快速表计算

![image-20210909160016033](https://img-blog.csdnimg.cn/img_convert/627759a8c66ea6a4bd8caeb91228ca88.png)

#### 1.4.2 自定义表计算

![image-20210909160515241](https://img-blog.csdnimg.cn/img_convert/690c60ba86b594165ddd8889db2bb731.png)

#### 1.4.3 计算新变量方式添加表计算

(1)

![image-20210909161133103](https://img-blog.csdnimg.cn/img_convert/a9a09752fd72c754aaa0f4a42cebcafd.png)

(2)

![image-20210909161221208](https://img-blog.csdnimg.cn/img_convert/43e1b62519826c93a5fe27b58b16821a.png)

## 二. 详细级别表达式

### 2.1 表达式级别

![image-20220110213255704](https://img-blog.csdnimg.cn/img_convert/56f24d0472f386f2bc921564071c48c6.png)

### 2.2 什么是详细级别表达式

![image-20220110213339887](https://img-blog.csdnimg.cn/img_convert/fd83dea8f9f569e6f32884a1fd56a246.png)

### 2.3 FIXED

![image-20220110213358288](https://img-blog.csdnimg.cn/img_convert/438755859ea5cc5e3e454d5fdc856a0e.png)

### 2.4 INCLUDE

![image-20220110213427145](https://img-blog.csdnimg.cn/img_convert/6ff7fa584e9ce92f0b5472ea7789f87f.png)

### 2.5 EXCLUDE

![image-20220110213437863](https://img-blog.csdnimg.cn/img_convert/ee6f50eaf88c32c36fc5b5984baf0289.png)

### 2.6 全表范围

**LOD 表达式的类型:全表范围**

![image-20220111105620930](https://img-blog.csdnimg.cn/img_convert/cbbe34d3299a71b034000064c28d428e.png)

### 2.7 注意事项

![image-20220110213513842](https://img-blog.csdnimg.cn/img_convert/f2761c5762daae4ab8cc74a3e0fb32b6.png)

## 三. 动作

### 3.1 集动作

-   集动作使得用户在与可视化项或仪表板交互时可以直接更改集值
    -   为集分配值、将值添加到集、从集中移除值
-   集动作的一般步骤
    -   创建一个或多个集
    -   创建一个集动作,该动作使用某一个集
    -   可选:创建使用集的计算字段
    -   构建一个可视化项,该可视化项使用集动作所引用的集
    -   测试并修改集动作

#### 3.1.1 选择性数据下钻展示

![image-20210910122616279](https://img-blog.csdnimg.cn/img_convert/813fd8c91d27c01e740924ad69bc8a18.png)

步骤：

![image-20210910122735480](https://img-blog.csdnimg.cn/img_convert/f52116ab30488070673eb50f4945c86c.png)

![image-20210910122829316](https://img-blog.csdnimg.cn/img_convert/f9694e4a8725442eb5c50f774bf26b79.png)

![image-20210910123031424](https://img-blog.csdnimg.cn/img_convert/067aeabd5aec6008c2c432d8d08ae3fe.png)

![image-20210910123256373](https://img-blog.csdnimg.cn/img_convert/44eba2fd76817e392846d6daf4a6c344.png)

#### 3.1.2 动态切换标色

![image-20210910123611505](https://img-blog.csdnimg.cn/img_convert/6afd09bb8950c574f27155c2f1dc6307.png)

![image-20210910123625857](https://img-blog.csdnimg.cn/img_convert/bcb76904d737b8a5361dadfd21cae4c8.png)

### 3.2 参数动作

![image-20220110214118364](https://img-blog.csdnimg.cn/img_convert/52d82016322ab7e1fde1f838c7a53920.png)

## 四. 外接 Python

### 4.1 直接外接 Python

![image-20220111104158183](https://img-blog.csdnimg.cn/img_convert/a4e6b2f99e3fb87d7d07585394447a26.png)

**按 tableau 调用的数据格式编写 python 代码**

```python
import numpy as np
#传入时使用单个值或者lst
a=[1,23,4]
b=[5.6,7,8]
#传出时为lst
np. add(np array(a), np array (b)). tolisto
```

**如何在 tableau 中调用 tably**

```
SCRIPT BOOL/INT/REAL/STRO
    需要调用的 python代码",依次给出使用的参数列表
    )# python代码中,参数依次用_arg1,arg2.进行标识

SCRIPT REAL(
    import numpy as np
    return np. add(np array( arg 1), np array( arg2 ). tolisto)
    avg(现状指数]),avg(预期指数]
    )
```

**注意**：**在 tableau 中调用 tabby 针对的是表计算级别!**

-   因此计算中完全适用寻址和分区概念
-   传送入 python 的数据是以每个单元格为单位先进行汇总
-   Tableau 会对每个分区调用一次分析扩展程序,因此传入数据时会按分区形成数据序列
-   由于是按照分区进行调用,因此需要注意计算量

### 4.2 python 预定义

环境加载

```
from tabpy tabpy tools client import Client
client=Client(http://localhost:9004/)
```

定义函数

```
import numpy as np
def ado(x,y):#由于要在 tableau中使用函数结果,函数必须要有 return值
return np. add(np array(x), nparray(y). tolisto
```

部署函数

```
client deploy (addo, add, 'Adds two numbers x and y)
在 python环境中测试函数
res client query (addo, a, b）
```

**在 tableau 中调用预定义函数**

```python
SCRIPT REAL(

return tabpy query (addo, arg1, arg2)Response]

avg(现状指数]),ag([预期指数]
```

**再次强调:在 tableau 中调用 tabby 针对的是表计算级别**

当沿着表横穿时,会将该行单元格汇总结果形成 list 进行传送,那么考虑一下它是如何实现计算的?

```python
SCRIPT REAL(

import numpy as np

return np corrcoef( arg1, arg2)[0, 1

avg(现状指数]),avg(顶预期指数])
```
