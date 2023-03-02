---
title: Tableau学习Step5一表计算、详细级别表达式、动作、外接python
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
abbrlink: 220202ae
date: 2022-02-02 22:07:59
summary: 表计算、详细级别表达式、动作、外接python,什么是表计算,是特殊类型的计算字段
img:
password:
---
# Tableau学习Step5一表计算、详细级别表达式、动作、外接python

## 一. 表计算

### 1.1 什么是表计算

- 是特殊类型的计算字段
- 根据当前的可视化内容（基于当前内容构建的虚拟表）进行计算，如排名、汇总、差分、定基比/环比.......
- 表计算并不考虑当前可视化内容中被筛选掉的任何度量或维度
- 表计算的结果并不影响数据源中的数据表

![image-20220111103908879](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220111103908879.png)



### 1.2 分区与寻址

- 分区字段
    - 用于定义计算组方式(确定执行表计算所针对的数据范围)的维度
    - 分区字段将视图拆分成多个子视图(或子表),系统在每个分区内单独执行表计算

- 寻址字段

- 执行表计算所需要使用的其余维度
- 用于确定计算时的移动方向
    - 横穿(从左到右)
    - 向下(从上到下)
    - 横穿,然后向下
    - 向下,然后横穿

#### 1.2.1 横穿 VS 向下

![image-20220111103814918](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220111103814918.png)

#### 1.2.2 横穿,然后向下 VS 向下,然后横穿

![image-20220111103940525](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220111103940525.png)

#### 1.2.3 加入分区维度

![image-20220111104012802](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220111104012802.png)



#### 1.2.4 单元格内计算与特殊级别

![image-20220111104040224](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220111104040224.png)



### 1.3 表计算常见类型

![image-20220110212928540](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220110212928540.png)



### 1.4 如何创建表计算

#### 1.4.1 快速表计算

![image-20210909160016033](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20210909160016033.png)





#### 1.4.2 自定义表计算

![image-20210909160515241](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20210909160515241.png)

#### 1.4.3 计算新变量方式添加表计算

(1)

![image-20210909161133103](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20210909161133103.png)

(2)

![image-20210909161221208](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20210909161221208.png)





## 二. 详细级别表达式

### 2.1 表达式级别

![image-20220110213255704](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220110213255704.png)



### 2.2 什么是详细级别表达式

![image-20220110213339887](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220110213339887.png)



### 2.3 FIXED

![image-20220110213358288](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220110213358288.png)

### 2.4 INCLUDE

![image-20220110213427145](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220110213427145.png)

### 2.5 EXCLUDE

![image-20220110213437863](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220110213437863.png)

### 2.6 全表范围

**LOD表达式的类型:全表范围**

![image-20220111105620930](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220111105620930.png)



### 2.7 注意事项

![image-20220110213513842](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220110213513842.png)





## 三. 动作

### 3.1 集动作

- 集动作使得用户在与可视化项或仪表板交互时可以直接更改集值
    - 为集分配值、将值添加到集、从集中移除值
- 集动作的一般步骤
    - 创建一个或多个集
    - 创建一个集动作,该动作使用某一个集
    - 可选:创建使用集的计算字段
    - 构建一个可视化项,该可视化项使用集动作所引用的集
    - 测试并修改集动作

#### 3.1.1 选择性数据下钻展示

![image-20210910122616279](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20210910122616279.png)

步骤：

![image-20210910122735480](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20210910122735480.png)

![image-20210910122829316](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20210910122829316.png)

![image-20210910123031424](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20210910123031424.png)

![image-20210910123256373](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20210910123256373.png)







#### 3.1.2 动态切换标色

![image-20210910123611505](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20210910123611505.png)

![image-20210910123625857](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20210910123625857.png)







### 3.2 参数动作



![image-20220110214118364](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220110214118364.png)

## 四. 外接Python

### 4.1 直接外接Python

![image-20220111104158183](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Tableau/TableauStudy05/image-20220111104158183.png)



**按 tableau调用的数据格式编写 python代码**

```python
import numpy as np
#传入时使用单个值或者lst
a=[1,23,4]
b=[5.6,7,8]
#传出时为lst
np. add(np array(a), np array (b)). tolisto
```





**如何在tableau中调用tably**

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

**注意**：**在 tableau中调用 tabby针对的是表计算级别!**

- 因此计算中完全适用寻址和分区概念
- 传送入 python的数据是以每个单元格为单位先进行汇总
- Tableau会对每个分区调用一次分析扩展程序,因此传入数据时会按分区形成数据序列
- 由于是按照分区进行调用,因此需要注意计算量





### 4.2 python预定义

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



**在 tableau中调用预定义函数**

```python
SCRIPT REAL(

return tabpy query (addo, arg1, arg2)Response]

avg(现状指数]),ag([预期指数]
```

**再次强调:在 tableau中调用 tabby针对的是表计算级别**

当沿着表横穿时,会将该行单元格汇总结果形成list进行传送,那么考虑一下它是如何实现计算的?

```python
SCRIPT REAL(

import numpy as np

return np corrcoef( arg1, arg2)[0, 1

avg(现状指数]),avg(顶预期指数])
```

