---
title: CSS简介，基础选择器，字体属性，文本属性
author: Sankey
coverImg: /medias/banner/1.jpg
top: false
cover: false
toc: true
mathjax: false
tags:
    - 前端
    - CSS
categories:
    - 技能之树
reprintPolicy: cc_by
img: /medias/posts/8.jpg
date: 2022-03-11 16:15:23
summary:
abbrlink: 202203111615
password:
---

# CSS 简介，基础选择器，字体属性，文本属性

博客园主页：[博客园主页-冰山一树 Sankey](https://www.cnblogs.com/bingshanyishu)
CSDN 主页：[CSDN 主页-冰山一树 Sankey](https://blog.csdn.net/m0_59464010)

> 前端学习：学习地址：[黑马程序员 pink 老师前端入门教程，零基础必看的 h5(html5)+css3+移动](https://www.bilibili.com/video/BV14J4114768?from=search&seid=8917517766284511711)，下面这些都是一些学习笔记。临渊羡鱼，不如退而结网！！愿我自己学有所成，也愿每个前端爱好者学有所成

## 一. CSS 简介

### 1.1 HTML 的局限性

![image-20211030220256724](https://img-blog.csdnimg.cn/img_convert/97f5625c8ab033fe6c43d268c9e2f3a7.png)

### 1.2 CSS—网页的美容师

-   CSS 是层叠样式表 ( Cascading Style Sheets ) 的简称.有时我们也会称之为 CSS 样式表或级联样式表。
-   CSS 是也是一种标记语言
-   CSS 主要用于设置 HTML 页面中的文本内容（字体、大小、对齐方式等）、图片的外形（宽高、边框样式、
    边距等）以及版面的布局和外观显示样式。
-   CSS 让我们的网页更加丰富多彩，布局更加灵活自如。简单理解：CSS 可以美化 HTML , 让 HTML 更漂亮，
    让页面布局更简单。

![image-20220308193753704](https://img-blog.csdnimg.cn/img_convert/08aa02666fa3f500525987f2e796ff83.png)

**总结**:

1. HTML 主要做结构,显示元素内容.
2. CSS 美化 HTML ,布局网页.
3. CSS 最大价值: 由 HTML 专注去做结构呈现，样式交给 CSS，即 结构 ( HTML ) 与样式( CSS ) 相分离

### 1.3 CSS 语法规范

使用 HTML 时，需要遵从一定的规范，CSS 也是如此。要想熟练地使用 CSS 对网页进行修饰，首先需要了解
CSS 样式规则。
CSS 规则由两个主要的部分构成：选择器以及一条或多条声明。

![image-20220308193859104](https://img-blog.csdnimg.cn/img_convert/f5fdfc0fae3c52948e2172f95b0f42e7.png)

-   选择器是用于指定 CSS 样式的 HTML 标签，花括号内是对该对象设置的具体样式
-   属性和属性值以“键值对”的形式出现
-   属性是对指定的对象设置的样式属性，例如字体大小、文本颜色等
-   属性和属性值之间用英文“:”分开
-   多个“键值对”之间用英文“;”进行区分

所有的样式，都包含在 `<style>` 标签内，表示是样式表。`<style>` 一般写到 `</head>` 上方。

```css
<head>
     <style>
         h4 {
         color: blue;
         font-size: 100px;
         }
     </style>
</head>
```

## 二. CSS 代码风格

以下代码书写风格不是强制规范,而是符合实际开发书写方式

### 2.1 样式格式书写

1.紧凑格式

```css
h3 {
    color: deeppink;
    font-size: 20px;
}
```

2.展开格式

```html
h3 { color: pink; font-size: 20px; }
```

强烈推荐第二种格式， 因为更直观。

### 2.2 样式大小写

```
h3 {
 color: pink;
}
```

```
H3 {
 COLOR: PINK;
}
```

强烈推荐样式选择器，属性名，属性值关键字全部使用**小写字母**，特殊情况除外。

### 2.2 样式空格风格

```css
h3 {
    color: pink;
}
```

① 属性值前面，冒号后面，保留一个空格

② 选择器（标签）和大括号中间保留空格

## 三. CSS 基础选择器

### 2.1 CSS 选择器的作用

选择器(选择符)就是根据不同需求把不同的标签选出来这就是选择器的作用。 简单来说，就是选择标签用的。

![image-20220308193859104](https://img-blog.csdnimg.cn/img_convert/f5fdfc0fae3c52948e2172f95b0f42e7.png)

以上 CSS 做了两件事：

1. 找到所有的 h1 标签。 选择器（选对人）。
2. 设置这些标签的样式，比如颜色为红色（做对事）。

### 2.2 选择器的分类

选择器分为基础选择器和复合选择器两个大类，我们这里先讲解一下基础选择器。

-   基础选择器是由单个选择器组成的
-   基础选择器又包括：标签选择器、类选择器、id 选择器和通配符选择器

| 基础选择器   | 作用                           | 特点                                  | 使用情况       | 用法               |
| ------------ | ------------------------------ | ------------------------------------- | -------------- | ------------------ |
| 标签选择器   | 可以选出所有相同的标签，比如 p | 不能差异化选择                        | 较多           | p {color: red;}    |
| 类选择器     | 可以选出 1 个或者多个标签      | 可以根据需求选择                      | 非常多         | .nav {color: red;} |
| id 选择器    | 一次只能选择 1 个标签          | ID 属性只能在每个 HTML 文档中出现一次 | 一般和 js 搭配 | #nav {color: red;} |
| 通配符选择器 | 选择所有的标签                 | 选择的太多，有部分不需要              | 特殊情况使用   | \* {color: red;}   |

### 2.3 标签选择器

标签选择器（元素选择器）是指用 HTML 标签名称作为选择器，按标签名称分类，为页面中某一类标签指定统一的 CSS 样式。

```css
标签名 {
    属性1: 属性值1;
    属性2: 属性值2;
    属性3: 属性值3;
    ...;
}
```

**作用**
标签选择器可以把某一类标签全部选择出来，比如所有的 <div> 标签和所有的 <span> 标签。
**优点**
能快速为页面中同类型的标签统一设置样式。
**缺点**
不能设计差异化样式，只能选择全部的当前标签。

### 2.4 类选择器

#### 2.4.1 语法

如果想要差异化选择不同的标签，单独选一个或者某几个标签，可以使用类选择器.

**语法**

```css
.类名 {
    属性1: 属性值1;
    ...;
}
```

例如，将所有拥有 red 类的 HTML 元素均为红色。

```css
.red {
    color: red;
}
```

**注意**：

-   类选择器使用“.”（英文点号）进行标识，后面紧跟类名（自定义，我们自己命名的）。
-   可以理解为给这个标签起了一个名字，来表示。
-   长名称或词组可以使用中横线来为选择器命名。
-   不要使用纯数字、中文等命名，尽量使用英文字母来表示。
-   命名要有意义，尽量使别人一眼就知道这个类名的目的。
-   命名规范：见附件（ Web 前端开发规范手册.doc）

**小案例：**

![image-20211030224349092](https://img-blog.csdnimg.cn/img_convert/5c96a15d67924bc63fc003197f7b1dbd.png)

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>画盒子</title>
    <style>
        .red {
            width: 100px;
            height: 100px;
            background-color: red;
        }
        .green {
            width: 100px;
            height: 100px;
            background-color: green;
        }
    </style>
</head>
<body>
    <div class="red"></div>
    <div class="green"></div>
    <div class="red"></div>
</body>
</html>
```

#### 2.4.2 多类名

我们可以给一个标签指定多个类名，从而达到更多的选择目的。 这些类名都可以选出这个标签. 简单理解就是一个标签有多个名字.

![image-20211031124055590](https://img-blog.csdnimg.cn/img_convert/900aa623ae2004a2da0e62b7a9542394.png)

1. 多类名使用方式

```
<div class="red font20">亚瑟</div>
```

-   在标签 class 属性中写 多个类名
-   多个类名中间必须用空格分开
-   这个标签就可以分别具有这些类名的样式

2. 多类名开发中使用场景

-   可以把一些标签元素相同的样式(共同的部分)放到一个类里面.
-   这些标签都可以调用这个公共的类,然后再调用自己独有的类.
-   从而节省 CSS 代码,统一修改也非常方便

### 2.5 id 选择器

id 选择器可以为标有特定 id 的 HTML 元素指定特定的样式。
HTML 元素以 id 属性来设置 id 选择器，CSS 中 id 选择器以“#" 来定义。

语法：

```
#id名 {
 属性1: 属性值1;
 ...
}
```

例如，将 id 为 nav 元素中的内容设置为红色。

```html
#nav { color:red; }
```

**id 选择器和类选择器的区别**

-   类选择器（class）好比人的名字，一个人可以有多个名字，同时一个名字也可以被多个人使用。
-   id 选择器好比人的身份证号码，全中国是唯一的，不得重复。
-   id 选择器和类选择器最大的不同在于使用次数上。
-   类选择器在修改样式中用的最多，id 选择器一般用于页面唯一性的元素上，经常和 JavaScript 搭配使用。

![image-20220308202234407](https://img-blog.csdnimg.cn/img_convert/7696fb97b458cf23c7eee1d3bd6a915a.png)

### 2.6 通配符选择器

在 CSS 中，通配符选择器使用“**\***”定义，它表示选取页面中所有元素（标签）。

```css
* {
    属性1: 属性值1;
    ...;
}

* {
    margin: 0;
    padding: 0;
}
```

-   通配符选择器不需要调用， 自动就给所有的元素使用样式
-   特殊情况才使用，后面讲解使用场景(以下是清除所有的元素标签的内外边距,后期讲)

```html
* { margin: 0; padding: 0; }
```

## 四. CSS 字体属性

CSS Fonts (字体)属性用于定义字体系列、大小、粗细、和文字样式（如斜体）。

### 4.1 字体系列

CSS 使用 `font-family` 属性定义文本的字体系列。

```html
p { font-family:"微软雅黑";} div {font-family: Arial,"Microsoft Yahei",
"微软雅黑";} body {font-family: 'Microsoft YaHei',tahoma,arial,'Hiragino Sans
GB'; }
```

-   各种字体之间必须使用英文状态下的逗号隔开
-   一般情况下,如果有空格隔开的多个单词组成的字体,加引号.
-   尽量使用系统默认自带字体，保证在任何用户的浏览器中都能正确显示
-   最常见的几个字体：body {font-family: 'Microsoft YaHei',tahoma,arial,'Hiragino Sans GB'; }

### 4.2 字体大小

CSS 使用 `font-size` 属性定义字体大小。

```css
p {
    font-size: 20px;
}
```

-   px（像素）大小是我们网页的最常用的单位
-   谷歌浏览器默认的文字大小为 16px
-   不同浏览器可能默认显示的字号大小不一致，我们尽量给一个明确值大小，不要默认大小
-   可以给 body 指定整个页面文字的大小

### 4.3 字体粗细

CSS 使用 font-weight 属性设置文本字体的粗细。

```
p {
 font-weight: bold;
}
```

| 属性值   | 描述                                                           |
| -------- | -------------------------------------------------------------- |
| normal   | 默认值（不加粗的）                                             |
| bold     | 定义粗体（加粗的）                                             |
| 100－900 | 400 等同于 normal，而 700 等同于 bold 注意这个数字后面不跟单位 |

-   可实现让加粗标签（比如 h 和 strong 等) 不加粗，或者其他标签加粗
-   实际开发时，更喜欢用数字表示粗细

### 4.4 文字样式

CSS 使用 font-style 属性设置文本的风格。

```
p {
 font-style: normal;
}
```

| 属性值 | 作用                                                     |
| ------ | -------------------------------------------------------- |
| normal | 默认值，浏览器会显示标准的字体样式 font－style：normal； |
| italic | 浏览器会显示斜体的字体样式。                             |

注意： 平时很少给文字加斜体，反而要给**斜体标签（em，i）**改为**不倾斜字体**。

### 4.5 复合属性

字体属性可以把以上文字样式综合来写, 这样可以更节约代码:

```
body {
 font: font-style font-weight font-size/line-height font-family;
}
```

-   使用 font 属性时，必须按上面语法格式中的顺序书写，不能更换顺序，并且各个属性间以空格隔开
-   不需要设置的属性可以省略（取默认值），但必须**保留 font-size 和 font-family 属性**，否则 font 属性将不起作用

```css
<style>
       /* 想要div文字变倾斜 加粗 字号设置为16像素 并且 是微软雅黑 */
       div {
           /* font-style: italic;
           font-weight: 700;
           font-size: 16px;
           font-family: 'Microsoft yahei'; */
           /* 复合属性: 简写的方式  节约代码 */
           /* font: font-style  font-weight  font-size/line-height  font-family; */
           /* font: italic 700 16px 'Microsoft yahei'; */
           font: 20px '黑体';
       		}
</style>
```

## 五. CSS 文本属性

CSS Text（文本）属性可定义文本的外观，比如文本的颜色、对齐文本、装饰文本、文本缩进、行间距等。

### 5.1 文本颜色

color 属性用于定义文本的颜色。

```css
div {
    color: red;
}
```

| 表示           | 属性值                             |
| -------------- | ---------------------------------- |
| 预定义的颜色值 | red，green，blue 等等              |
| 十六进制       | ＃FF0000，＃FF6600，＃29D794       |
| RGB 代码       | rgb(255,0,0)或 rgb(100％,0％,0％） |

### 5.2 对齐文本

text-align 属性用于设置元素内文本内容的水平对齐方式。

```html
div { text-align: center; }
```

| 属性值 | 解释             |
| ------ | ---------------- |
| left   | 左对齐（默认值） |
| right  | 右对齐           |
| center | 居中对齐         |

### 5.3 装饰文本

**text-decoration** 属性规定添加到文本的修饰。可以给文本添加下划线、删除线、上划线等。

```css
div {
 text-decoration：underline；
}
```

| 属性值        | 描述                              |
| ------------- | --------------------------------- |
| none          | 默认。没有装饰线（最常用）        |
| underline     | 下划线。链接 a 自带下划线（常用） |
| overline      | 上划线。（几乎不用）              |
| line－through | 删除线。（不常用）                |

### 5.4 文本缩进

**text-indent** 属性用来指定文本的第一行的缩进，通常是将段落的首行缩进。

![image-20211031133257859](https://img-blog.csdnimg.cn/img_convert/5a7335f2c148c38126a47d7de614e0db.png)

```
div {
 text-indent: 10px;
}
```

通过设置该属性，所有元素的第一行都可以缩进一个给定的长度，甚至该长度可以是负值。

```
p {
 text-indent: 2em;
}
```

**em** 是一个相对单位，就是当前元素`font-size` 1 个文字的大小, 如果当前元素没有设置大小，则会按照父元
素的 1 个文字大小。

### 5.5 行间距

![image-20211031133702371](https://img-blog.csdnimg.cn/img_convert/c0996ad2f0560ed869382a588a93122a.png)

**line-height** 属性用于设置行间的距离（行高）。可以控制文字行与行之间的距离.一般可用于文字垂直居中显示

```html
p { line-height: 26px; }
```

## 六. CSS 的引入方式

按照 CSS 样式书写的位置（或者引入的方式），CSS 样式表可以分为三大类：

1. 行内样式表（行内式）
2. 内部样式表（嵌入式）
3. 外部样式表（链接式）

### 6.1 内部样式表

内部样式表（内嵌样式表）是写到 html 页面内部. 是将所有的 CSS 代码抽取出来，单独放到一个 `<style>` 标签中。

```css
<style>
 div {
 color: red;
 font-size: 12px;
 }
</style>
```

-   `<style>` 标签理论上可以放在 HTML 文档的任何地方，但一般会放在文档的`<head>`标签中
-   通过此种方式，可以方便控制当前整个页面中的元素样式设置
-   代码结构清晰，但是并没有实现结构与样式完全分离
-   使用内部样式表设定 CSS，通常也被称为嵌入式引入，这种方式是我们练习时常用的方式

### 6.2 行内样式表

行内样式表（内联样式表）是在元素标签内部的 style 属性中设定 CSS 样式。适合于修改简单样式.

```css
<div style="color: red; font-size: 12px;">青春不常在，抓紧谈恋爱</div>
```

-   style 其实就是标签的属性
-   在双引号中间，写法要符合 CSS 规范
-   可以**控制当前的标签设置样式**
-   由于书写繁琐，并且没有体现出结构与样式相分离的思想，所以不推荐大量使用，只有对当前元素添加简
    单样式的时候，可以考虑使用
-   使用行内样式表设定 CSS，通常也被称为**行内式引入**

### 6.3 外部样式表

实际开发都是外部样式表. 适合于样式比较多的情况. 核心是:样式单独写到 CSS 文件中，之后把 CSS 文件引入
到 HTML 页面中使用，通常也被称为外链式或链接式引入。

引入外部样式表分为两步：

1. 新建一个后缀名为 .css 的样式文件，把所有 CSS 代码都放入此文件中。
2. 在 HTML 页面中，使用`<link>` 标签引入这个文件。

```css
<link rel="stylesheet" href="css文件路径">
```

| 属性 | 作用                                                                                                |
| ---- | --------------------------------------------------------------------------------------------------- |
| rel  | 定义当前文档与被链接文档之间的关系,在这里需要指定为"stylesheet'",表示被链接的文档是一个样式表文件。 |
| href | 定义所链接外部样式表文件的 UL,可以是相对路径,也可以是绝对路径。                                     |

## 七. 综合案例

制作一个新闻页

![image-20220308204224035](https://img-blog.csdnimg.cn/img_convert/714f5ab969db04f1820108feced890a9.png)

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <meta http-equiv="X-UA-Compatible" content="ie=edge" />
        <title>Document</title>
        <style>
            body {
                font: 16px/28px 'Microsoft YaHei';
            }
            h1 {
                /* 文字不加粗 */
                font-weight: 400;
                /* 让h1里面的文字水平居中对齐 */
                text-align: center;
            }
            a {
                text-decoration: none;
            }
            .gray {
                color: #888888;
                font-size: 12px;
                text-align: center;
            }
            .search {
                color: #666;
                /* #666666     #666
           #ff00ff    #f0f */
                width: 170px;
            }
            .btn {
                font-weight: 700;
            }
            p {
                /* 首行缩进2个字的距离 */
                text-indent: 2em;
            }
            .pic {
                /* 想要图片居中对齐,则是让它的父亲 p标签添加 水平居中的代码 */
                text-align: center;
            }
            .footer {
                color: #888888;
                font-size: 12px;
            }
        </style>
    </head>
    <body>
        <h1>北方高温明日达鼎盛 京津冀多地地表温度将超60℃</h1>
        <div class="gray">
            2019-07-03 16:31:47 来源: <a href="#">中国天气网</a>　
            <input type="text" value="请输入查询条件..." class="search" />
            <button class="btn">搜索</button>
        </div>
        <hr />
        <p>
            中国天气网讯
            今天（3日），华北、黄淮多地出现高温天气，截至下午2点，北京、天津、郑州等地气温突破35℃。预报显示，今后三天（3-5日），这一带的高温天气将继续发酵，高温范围以及强度将在4日达到鼎盛，预计北京、天津、石家庄、济南等地明天的最高气温有望突破38℃，其中北京和石家庄的最高气温还有望创今年以来的新高。
        </p>

        <h4>气温41.4℃！地温66.5！北京强势迎七月首个高温日</h4>
        <p class="pic">
            <img src="images/pic.jpeg" alt="" />
        </p>
        <p>
            今天，华北、黄淮一带的高温持续发酵，截至今天下午2点，陕西北部、山西西南部、河北南部、北京、天津、山东西部、河南北部最高气温已普遍超过35℃。大城市中，北京、天津、郑州均迎来高温日。
        </p>

        <p>
            在阳光暴晒下，地表温度也逐渐走高。今天下午2点，华北黄淮大部地区的地表温度都在50℃以上，部分地区地表温度甚至超过60℃。其中，河北衡水地表温度高达68.3℃，天津站和北京站附近的地表温度分别高达66.6℃和66.5℃。
        </p>

        <h4>明日热度再升级！京津冀携手冲击38℃+</h4>
        <p>
            中国天气网气象分析师王伟跃介绍，明天（4日），华北、黄淮地区35℃以上的高温天气还将继续升级，并进入鼎盛阶段，高温强度和范围都将发展到最强。
            明天，北京南部、天津大部、河北中部和南部、山东中部和西部、山西南部局地、河南北部、东北部分地区的最高气温都将达到或超过35℃。
        </p>

        <p>
            不过，专家提醒，济南被雨水天气完美绕开，因此未来一周，当地的高温还会天天上岗。在此提醒当地居民注意防暑降温，防范持续高温带来的各种不利影响。（文/张慧
            数据支持/王伟跃 胡啸 审核/刘文静 张方丽）
        </p>

        <p class="footer">本文来源：中国天气网 责任编辑：刘京_NO5631</p>
    </body>
</html>
```
