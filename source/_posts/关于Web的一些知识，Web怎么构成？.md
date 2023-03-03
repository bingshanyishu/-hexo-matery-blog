---
title: 关于Web的一些知识，Web怎么构成？
author: Breezs
coverImg: /medias/banner/1.jpg
top: false
cover: false
toc: true
mathjax: false
tags:
    - 前端
categories:
    - 技能之树
reprintPolicy: cc_by
img: /medias/posts/6.jpg
date: 2022-03-09 18:29:01
summary:
abbrlink: 202203091829
password:
---

# 关于 Web 的一些知识，Web 怎么构成？

> 前端学习：学习地址：[黑马程序员 pink 老师前端入门教程，零基础必看的 h5(html5)+css3+移动](https://www.bilibili.com/video/BV14J4114768?from=search&seid=8917517766284511711)，下面这些都是一些学习笔记。临渊羡鱼，不如退而结网！！愿我自己学有所成，也愿每个前端爱好者学有所成

## 一. 网页

### 1.1 什么是网页

-   网站是指在因特网上根据一定的规则，使用 HTML 等制作的用于展示特定内容相关的网页集合。
-   网页是网站中的一“页”，通常是 HTML 格式的文件，它要通过浏览器来阅读。
-   网页是构成网站的基本元素，它通常由图片、链接、文字、声音、视频等元素组成。通常我们看到的网页， 常见.html 后缀结尾的文件，因此将其俗称为 HTML 文件。

### 1.2 什么是 HTML

**HTML** 指的是超文本标记语言 **(Hyper Text Markup Language)** ，它是用来描述网页的一种语言。 HTML **不是一种编程语言**，而是一种**标记语言** (markup language)。 标记语言是一套标记标签 (markup tag)。

**所谓超文本，有 2 层含义**：

1. 它可以加入图片、声音、动画、多媒体等内容（超越了文本限制 ）。
2. 它还可以从一个文件跳转到另一个文件，与世界各地主机的文件连接（超级链接文本 ）。

### 1.3 网页的形成

网页是由网页元素组成的，这些元素是利用 html 标签描述出来，然后通过浏览器解析来显示给用户的。

![image-20211029214501104](https://img-blog.csdnimg.cn/img_convert/9c41b54081791ca2fb6f75c9f0a6ef61.png)

## 二. 浏览器

### 2.1 常用浏览器

浏览器是网页显示、运行的平台。常用的浏览器有 IE、火狐（Firefox）、谷歌（Chrome）、Safari 和 Opera 等。平时称为五大浏览器。

![image-20220307220350672](https://img-blog.csdnimg.cn/img_convert/fb81b6ec8775f8b1fd6a6234fd1ce2f6.png)

### 2.2 浏览器内核

浏览器内核（渲染引擎）： 负责读取网页内容，整理讯息，计算网页的显示方式并显示页面。

![image-20220307220545531](https://img-blog.csdnimg.cn/img_convert/779e9eac0a44e6056d7bad189811b442.png)

### 2.3 浏览器私有前缀

![image-20211128133032407](https://img-blog.csdnimg.cn/img_convert/87d249a3890e3edacfa05f81ff82a7f9.png)

## 三. Web 标准

Web 标准是由 W3C 组织和其他标准化组织制定的一系列标准的集合。W3C（万维网联盟）是国际最著名的标准化组织。

### 3.1 为什么需要 web 标准

![image-20211029215028080](https://img-blog.csdnimg.cn/img_convert/4ff89326e2643bdc987a915235c7ddd9.png)

遵循 Web 标准除了可以让不同的开发人员写出的页面更标准、更统一外，还有以下优点：

-   让 Web 的发展前景更广阔。
-   内容能被更广泛的设备访问。
-   更容易被搜寻引擎搜索。
-   降低网站流量费用。
-   使网站更易于维护。
-   提高页面浏览速度。

### 3.2 Web 标准的构成

主要包括结构（Structure） 、表现（Presentation）和行为（Behavior）三个方面。

| 标准 |                              解释                               |
| :--: | :-------------------------------------------------------------: |
| 结构 |       结构用于对网页元素进行整理和分类，现阶段主要学 HTML       |
| 表现 | 表现用于设置网页元素的版式、颜色、大小等外观形式，主要是指 CSS  |
| 行为 | 行为是指网页模型的定义及交互的编写，现阶段主要学的是 JavaScript |

Web 标准提出的最佳体验方案：**结构、样式、行为相分离**。

**简单理解**： 结构写到 HTML 文件中， 表现写到 CSS 文件中， 行为写到 JavaScript 文件中。

![image-20211029215535213](https://img-blog.csdnimg.cn/img_convert/913ad3af54b827ed827e0a664621d25d.png)

## 四. 查阅文档

经常查阅文档是个非常好的习惯

推荐的网址：

-   百度：http://www.baidu.com
-   W3C：http://www.w3school.com.cn/
-   MDN：https://developer.mozilla.org/zh-CN/
