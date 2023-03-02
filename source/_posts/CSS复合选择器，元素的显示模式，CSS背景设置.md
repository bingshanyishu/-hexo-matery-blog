---
title: CSS复合选择器，元素的显示模式，CSS背景设置
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
img: /medias/posts/2.jpg
date: 2022-03-11 16:33:43
summary: 在 CSS 中，可以根据选择器的类型把选择器分为基础选择器和复合选择器，复合选择器是建立在基础选择器之上，对基本选择器进行组合形成的。
abbrlink: 20220311163343
password:
---

# CSS 复合选择器，元素的显示模式，CSS 背景设置

博客园主页：[博客园主页-冰山一树 Sankey](https://www.cnblogs.com/bingshanyishu)
CSDN 主页：[CSDN 主页-冰山一树 Sankey](https://blog.csdn.net/m0_59464010)

> 前端学习：学习地址：[黑马程序员 pink 老师前端入门教程，零基础必看的 h5(html5)+css3+移动](https://www.bilibili.com/video/BV14J4114768?from=search&seid=8917517766284511711)，下面这些都是一些学习笔记。临渊羡鱼，不如退而结网！！愿我自己学有所成，也愿每个前端爱好者学有所成

## 一. Emmet 语法

Emmet 语法前身是 Zen coding,它使用缩写来提高 html/css 的编写速度，Vscode 内部已经集成该语法。

**快速生成 HTML/CSS 结构语法**：

1. 生成标签，直接输入标签名按 tab 键即可比如 div 然后 tab 键，就可以生成`<div></div>`
2. 如果想要生成多个相同标签加上`*`就可以了 比如 `div*3`就可以快速生成 3 个 div
3. 如果有父子级关系的标签，可以用>比如 `ul>li`就可以了
4. 如果有兄弟关系的标签，用`+`就可以了比如`div+p`
5. 如果生成带有类名或者 id 名字的，直接写`.dema` 或者 `#two` tab 键就可以了
6. 如果生成的 div 类名是有顺序的，可以用`自增符号$`
7. 如果想要在生成的标签内部写内容可以用`{}`表示

## 二. 复合选择器

在 CSS 中，可以根据选择器的类型把选择器分为基础选择器和复合选择器，复合选择器是建立在基础选择器之上，对基本选择器进行组合形成的。

-   复合选择器可以更准确、更高效的选择目标元素（标签）
-   复合选择器是由两个或多个基础选择器，通过不同的方式组合而成的
-   常用的复合选择器包括：后代选择器、子选择器、并集选择器、伪类选择器等等

### 2.1 后代选择器

后代选择器又称为包含选择器，可以选择父元素里面子元素。其写法就是把外层标签写在前面，内层标签写在 后面，中间用空格分隔。当标签发生嵌套时，内层标签就成为外层标签的后代。

```
元素1 元素2 { 样式声明 }
```

上述语法表示选择元素 1 里面的所有元素 2 (后代元素)。

```html
/* 选择 ul 里面所有的 li标签元素 */ ul li { 样式声明 }
```

-   元素 1 和 元素 2 中间用**空格**隔开
-   元素 1 是父级，元素 2 是子级，最终选择的是元素 2
-   元素 2 可以是儿子，也可以是孙子等，只要是元素 1 的后代即可
-   元素 1 和 元素 2 可以是**任意基础选择器**

### 2.2 子选择器

子元素选择器（子选择器）只能选择作为某元素的最近一级子元素。简单理解就是选亲儿子元素

```
元素1 > 元素2 { 样式声明 }
```

上述语法表示选择元素 1 里面的所有直接后代(子元素) 元素 2。

```
/* 选择 div 里面所有最近一级 p 标签元素 */

div > p { 样式声明 }
```

-   元素 1 和 元素 2 中间用 大于号 隔开
-   元素 1 是父级，元素 2 是子级，最终选择的是元素 2
-   元素 2 必须是亲儿子，其孙子、重孙之类都不归他管. 你也可以叫他 亲儿子选择器

**将下面的链接文字修改为红色。**

```html
<div class="nav">
    <ul>
        <li><a href="#">百度</a></li>
        <li><a href="#">百度</a></li>
    </ul>
</div>

<style>
    .nav ul li a {
        color: red;
    }
</style>
```

**将下面的大肘子文字修改为红色。**

```html
<div class="hot">
    <a href="#">大肘子</a>
    <ul>
        <li><a href="#">猪头</a></li>
        <li><a href="#">猪尾巴</a></li>
    </ul>
</div>

<style>
    .hot > a {
        color: red;
    }
</style>
```

### 2.3 并集选择器

并集选择器可以选择多组标签, 同时为他们定义相同的样式。通常用于集体声明.
并集选择器是各选择器通过英文逗号（,）连接而成，任何形式的选择器都可以作为并集选择器的一部分。

```
元素1,元素2 { 样式声明 }
```

上述语法表示选择元素 1 和 元素 2。

```
 /* 选择 ul 和 div标签元素 */

ul,div { 样式声明 }
```

-   元素 1 和 元素 2 中间用逗号隔开
-   逗号可以理解为和的意思
-   并集选择器通常用于集体声明

![image-20211031145456517](https://img-blog.csdnimg.cn/img_convert/57e6d2d453e9cecbcc237b55189d4a0c.png)

### 2.4 伪类选择器

伪类选择器用于向某些选择器添加特殊的效果，比如给链接添加特殊效果，或选择第 1 个，第 n 个元素。
伪类选择器书写最大的特点是用冒号（:）表示，比如 :hover 、 :first-child 。
因为伪类选择器很多，比如有链接伪类、结构伪类等，所以这里先给大家讲解常用的链接伪类选择器。

#### 2.4.1 链接伪类选择器

```css
<style>
        /* 1.未访问的链接 a:link  把没有点击过的(访问过的)链接选出来 */
        a:link {
            color: #333;
            text-decoration: none;
        }

        /*2. a:visited 选择点击过的(访问过的)链接 */
        a:visited {
            color: orange;
        }

        /*3. a:hover 选择鼠标经过的那个链接 */
        a:hover {
            color: skyblue;
        }

        /* 4. a:active 选择的是我们鼠标正在按下还没有弹起鼠标的那个链接 */
        a:active {
            color: green;
        }
    </style>
```

**链接伪类选择器注意事项**

1. 为了确保生效，请按照 LVHA 的循顺序声明 :**link－:visited－:hover－:active。**
2. 记忆法：**love hate** 或者 **lv 包包 hao 。**
3. 因为 a 链接在浏览器中具有默认样式，所以我们实际工作中都需要给**链接单独指定样式。**

#### 2.4.2 :focus 伪类选择器

:focus 伪类选择器用于选取获得焦点的表单元素。
焦点就是光标，一般情况 `<input>` 类表单元素才能获取，因此这个选择器也主要针对于表单元素来说。

```css
input:focus {
    background-color: yellow;
}
```

## 三. 元素的显示模式

### 3.1 什么是元素显示模式

网页的标签非常多，在不同地方会用到不同类型的标签，了解他们的特点可以更好的布局我们的网页。

元素显示模式就是元素（标签）以什么方式进行显示，比如`<div>`自己占一行，比如一行可以放多个`<span>`。

HTML 元素一般分为块元素和行内元素两种类型

| 元素模式   | 元素排列               | 设置样式                 | 默认宽度         | 包含                     |
| ---------- | ---------------------- | ------------------------ | ---------------- | ------------------------ |
| 块级元素   | 一行只能放一个块级元素 | 可以设置宽度高度         | 容器的 100%      | 容器级可以包含任何标签   |
| 行内元素   | 一行可以放多个行内元素 | 不可以直接设置宽度和高度 | 它本身内容的宽容 | 容纳文本或则其他行内元素 |
| 行内块元素 | 一行放多个行内块元素   | 可以设置宽度和高度       | 它本身内容的宽容 |                          |

### 3.2 块元素

常见的块元素有`<h1>~<h6>、<p>、<div>、<ul>、<ol>、<li>`等，其中 `<div>` 标签是最典型的块元素。

**块级元素的特点**：

-   比较霸道，自己独占一行。
-   高度，宽度、外边距以及内边距都可以控制。
-   宽度默认是容器（父级宽度）的 100%。
-   是一个容器及盒子，里面可以放行内或者块级元素。

**注意**：

-   文字类的元素内不能使用块级元素
-   `<p>` 标签主要用于存放文字，因此 `<p>` 里面不能放块级元素，特别是不能放`<div>`
-   同理， `<h1>~<h6>`等都是文字类块级标签，里面也不能放其他块级元素

### 3.3 行内元素

常见的行内元素有 `<a>、<strong>、<b>、<em>、<i>、<del>、<s>、<ins>、<u>、<span>`等，其中`<span>` 标签是最典型的行内元素。有的地方也将行内元素称为内联元素。

**行内元素的特点**：

-   相邻行内元素在一行上，一行可以显示多个。
-   高、宽直接设置是无效的。
-   默认宽度就是它本身内容的宽度。
-   行内元素只能容纳文本或其他行内元素。

**注意**：

-   链接里面不能再放链接
-   特殊情况链接 `<a>` 里面可以放块级元素，但是给 `<a>` 转换一下块级模式最安全

### 3.4 行内块元素

在行内元素中有几个特殊的标签 —— `<img/>、<input/>、<td>`，它们同时具有块元素和行内元素的特点。有些资料称它们为行内块元素。

行内块元素的特点：

-   和相邻行内元素（行内块）在一行上，但是他们之间会有空白缝隙。一行可以显示多个（行内元素特点）。
-   默认宽度就是它本身内容的宽度（行内元素特点）。
-   高度，行高、外边距以及内边距都可以控制（块级元素特点）

### 3.5 元素显示模式转换

特殊情况下，我们需要元素模式的转换，简单理解: 一个模式的元素需要另外一种模式的特性
比如想要增加链接 `<a>` 的触发范围。

-   转换为块元素：`display:block`;
-   转换为行内元素：`display:inline`;
-   转换为行内块：`display: inline-block`;

案例：

![image-20211031225107609](https://img-blog.csdnimg.cn/img_convert/a8a7ca8e3c9dc62db93ace7e06b391f3.png)

```html
<style>
    /* 1. 把a转换为块级元素 */
    a {
        display: block;
        width: 230px;
        height: 40px;
        background-color: #55585a;
        font-size: 14px;
        color: #fff;
        text-decoration: none;
        text-indent: 2em;
        line-height: 40px;
    }

    /* 2 鼠标经过链接变换背景颜色 */
    a:hover {
        background-color: #ff6700;
    }
</style>

<body>
    <a href="#">手机 电话卡</a>
    <a href="#">电视 盒子</a>
    <a href="#">笔记本 平板</a>
    <a href="#">出行 穿戴</a>
    <a href="#">智能 路由器</a>
    <a href="#">健康 儿童</a>
    <a href="#">耳机 音响</a>
</body>
```

### 3.5 单行文字垂直居中

CSS 没有提供文字垂直居中的代码. 但可以使用一个小技巧来实现.
解决方案: 让文字的行高等于盒子的高度 就可以让文字在当前盒子内垂直居中

垂直居中的原理：

![image-20211102205217951](https://img-blog.csdnimg.cn/img_convert/1c2b7e56a6fded33f4b70290a2fd6218.png)

```html
line-height: 40px;
```

## 四. CSS 的背景

通过 CSS 背景属性，可以给页面元素添加背景样式。
背景属性可以设置**背景颜色、背景图片、背景平铺、背景图片位置、背景图像固定**等。

| 属性                  | 作用           | 值                                                             |
| --------------------- | -------------- | -------------------------------------------------------------- |
| background-color      | 背景颜色       | 预定义的颜色值/十六进制/RGB 代码                               |
| background-image      | 背景图片       | url(图片路径)                                                  |
| background-repeat     | 是否平铺       | repeat/no-repeat/repeat-x/repeat-y                             |
| background-position   | 背景位置       | length/position 分别是 x 和 y 坐标                             |
| background-attachment | 背景附着       | scroll(背景滚动)fxed(背景固定)                                 |
| 背景颜色半透明        | 背景颜色半透明 | background:rgba(0,0,0,0.3):后面必须是 4 个值                   |
| 背景简写              | 书写更简单     | 背景颜色 背景图片地址 背景平铺 背景滚动 背景位置; 中间空格隔开 |

接下来我们看看具体怎么使用

### 4.1 背景颜色

background-color 属性定义了元素的背景颜色。

```
background-color:颜色值;
```

一般情况下元素背景颜色默认值是 transparent（透明），我们也可以手动指定背景颜色为透明色。

```
background-color:transparent;
```

### 4.2 背景图片

background-image 属性描述了元素的背景图像。实际开发常见于 logo 或者一些装饰性的小图片或者是超
大的背景图片, 优点是非常便于控制位置. (精灵图也是一种运用场景)

```css
background-image: none | url (url);
```

| 参数值 | 作用                           |
| ------ | ------------------------------ |
| none   | 无背景图(默认的)               |
| url    | 使用绝对或相对地址指定背景图像 |

注意：

-   路径必须加引号
-   路径还必须是相对路径，绝对路径无法加载图片。

### 4.3 背景平铺

如果需要在 HTML 页面上对背景图像进行平铺，可以使用 background-repeat 属性。

```
background-repeat: repeat | no-repeat | repeat-x | repeat-y
```

| 参数值    | 作用                               |
| --------- | ---------------------------------- |
| repeat    | 背景图像在纵向和横向上平铺(默认的) |
| no-repeat | 背景图像不平铺                     |
| repeat-x  | 背景图像在横向上平铺               |
| repeat-y  | 背景图像在纵向平铺                 |

### 4.4 背景图片位置

装饰性图片不要插入图片，不好调节位置，使用背景图片

利用 background-position 属性可以改变图片在背景中的位置。

```
background-position: x y;
background-position：top bottom
```

参数代表的意思是：x 坐标和 y 坐标。 可以使用 方位名词 或者 精确单位

| 参数值   | 说明                                                        |
| -------- | ----------------------------------------------------------- |
| length   | 百分数 \| 由浮点数字和单位标识符组成的长度值                |
| position | top \| center \| bottom \| left \| center \| right 方位名词 |

1. 参数是方位名词
    - 如果指定的两个值都是方位名词，则两个值前后顺序无关，比如 left top 和 top left 效果一致
    - 如果只指定了一个方位名词，另一个值省略，则第二个值默认居中对齐
2. 参数是精确单位
    - 如果参数值是精确坐标，那么第一个肯定是 x 坐标，第二个一定是 y 坐标
    - 如果只指定一个数值，那该数值一定是 x 坐标，另一个默认垂直居中
3. 参数是混合单位
    - 如果指定的两个值是精确单位和方位名词混合使用，则第一个值是 x 坐标，第二个值是 y 坐标
4. **屏幕显示不完的超大图片，可使用 center top 来使图片最重要位置保持在最中间**

### 4.5 背景图像固定

background-attachment 属性设置背景图像是否固定或者随着页面的其余部分滚动。

background-attachment 后期可以制作视差滚动的效果。

```
background-attachment : scroll | fixed
```

| 参数   | 作用                     |
| ------ | ------------------------ |
| scroll | 背景图像是随对象内容滚动 |
| fixed  | 背景图像固定             |

### 4.6 背景复合写法

为了简化背景属性的代码，我们可以将这些属性合并简写在同一个属性 background 中。从而节约代码量.
当使用简写属性时，没有特定的书写顺序,一般习惯约定顺序为：
background: 背景颜色 背景图片地址 背景平铺 背景图像滚动 背景图片位置;

这是实际开发中，更提倡的写法。

```css
background: transparent url(image.jpg) repeat-y fixed top;
```

### 4.7 背景色半透明

CSS3 为我们提供了背景颜色半透明的效果。

```css
background: rgba(0, 0, 0, 0.3);
```

-   最后一个参数是 alpha 透明度，取值范围在 0~1 之间
-   我们习惯把 0.3 的 0 省略掉，写为 background: rgba(0, 0, 0, .3);
-   注意：背景半透明是指盒子背景半透明，盒子里面的内容不受影响
-   CSS3 新增属性，是 IE9+ 版本浏览器才支持的
-   但是现在实际开发,我们不太关注兼容性写法了,可以放心使用

## 五. 综合案例

![image-20211102214939680](https://img-blog.csdnimg.cn/img_convert/f5288370e4a1cf20aee3537938104e72.png)

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <meta http-equiv="X-UA-Compatible" content="ie=edge" />
        <title>综合案例-五彩导航</title>
        <style>
            .nav a {
                display: inline-block;
                width: 120px;
                height: 58px;
                background-color: pink;
                text-align: center;
                line-height: 48px;
                color: #fff;
                text-decoration: none;
            }

            .nav .bg1 {
                background: url(images/bg1.png) no-repeat;
            }

            .nav .bg1:hover {
                background-image: url(images/bg11.png);
            }

            .nav .bg2 {
                background: url(images/bg2.png) no-repeat;
            }

            .nav .bg2:hover {
                background-image: url(images/bg22.png);
            }
        </style>
    </head>

    <body>
        <div class="nav">
            <a href="#" class="bg1">五彩导航</a>
            <a href="#" class="bg2">五彩导航</a>
            <a href="#">五彩导航</a>
            <a href="#">五彩导航</a>
            <a href="#">五彩导航</a>
        </div>
    </body>
</html>
```
