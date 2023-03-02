---
title: CSS高级技巧——精灵图，字体图标，三角形等
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
img: /medias/posts/7.jpg
abbrlink: 202203122154
date: 2022-03-12 21:54:54
summary: 当网页中的图像过多时，服务器就会频繁地接收和发送请求图片，为了有效地减少服务器接收和发送请求的次数，提高页面的加载速度，出现了 **CSS 精灵技术**
password:
---

# CSS 高级技巧——精灵图，字体图标，三角形等

博客园主页：[博客园主页-冰山一树 Sankey](https://www.cnblogs.com/bingshanyishu)
CSDN 主页：[CSDN 主页-冰山一树 Sankey](https://blog.csdn.net/m0_59464010)

> 前端学习：学习地址：[黑马程序员 pink 老师前端入门教程，零基础必看的 h5(html5)+css3+移动](https://www.bilibili.com/video/BV14J4114768?from=search&seid=8917517766284511711)，下面这些都是一些学习笔记。临渊羡鱼，不如退而结网！！愿我自己学有所成，也愿每个前端爱好者学有所成

## 一. 精灵图

### 1.1 为什么需要精灵图

![image-20220309191941187](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309191941187.png)

![image-20211119214638056](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20211119214638056.png)

一个网页中往往会应用很多小的背景图像作为修饰，当网页中的图像过多时，服务器就会频繁地接收和发送请求图片，造成服务器请求压力过大，这将大大降低页面的加载速度。
因此，为了有效地减少服务器接收和发送请求的次数，提高页面的加载速度，出现了 **CSS 精灵技术**（也称**CSS Sprites、CSS 雪碧**）。
**核心原理**：将网页中的一些小背景图像整合到一张大图中 ，这样服务器只需要一次请求就可以了。

### 1.2 精灵图（sprites）的使用

使用精灵图核心：

1. 精灵技术主要针对于背景图片使用。就是把多个小背景图片整合到一张大图片中。
2. 这个大图片也称为 sprites 精灵图 或者 雪碧图
3. 移动背景图片位置， 此时可以使用 background-position 。
4. 移动的距离就是这个目标图片的 x 和 y 坐标。注意网页中的坐标有所不同
5. 因为一般情况下都是往上往左移动，所以数值是负值。
6. 使用精灵图的时候需要精确测量，每个小背景图片的大小和位置。

### 1.3 案例

这是一张精灵图图片，拼出单词`pink`

![abcd](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/abcd.jpg)

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <meta http-equiv="X-UA-Compatible" content="ie=edge" />
        <title>利用精灵图拼出pink</title>
        <style>
            span {
                display: inline-block;
                background: url(images/abcd.jpg) no-repeat;
            }
            .p {
                width: 100px;
                height: 112px;
                /* background-color: pink; */
                background-position: -493px -276px;
            }
            .i {
                width: 60px;
                height: 108px;
                /* background-color: pink; */
                background-position: -327px -142px;
            }
            .n {
                width: 108px;
                height: 109px;
                /* background-color: pink; */
                background-position: -215px -141px;
            }
            .k {
                width: 105px;
                height: 114px;
                /* background-color: pink; */
                background-position: -495px -142px;
            }
        </style>
    </head>
    <body>
        <span class="p"></span>
        <span class="i"></span>
        <span class="n"></span>
        <span class="k"></span>
    </body>
</html>
```

## 二. 字体图标

### 2.1 字体图标的产生

字体图标使用场景： 主要用于显示网页中通用、常用的一些小图标

精灵图是有诸多优点的，但是缺点很明显。

-   图片文件还是比较大的。
-   图片本身放大和缩小会失真。
-   一旦图片制作完毕想要更换非常复杂。

此时，有一种技术的出现很好的解决了以上问题，就是**字体图标 iconfont**。
字体图标可以为前端工程师提供一种方便高效的图标使用方式，展示的是图标，本质属于字体。

### 2.2 字体图标的优点

-   轻量级：一个图标字体要比一系列的图像要小。一旦字体加载了，图标就会马上渲染出来，减少了服务器请求
-   灵活性：本质其实是文字，可以很随意的改变颜色、产生阴影、透明效果、旋转等
-   兼容性：几乎支持所有的浏览器，请放心使用

注意： 字体图标不能替代精灵技术，只是对工作中图标部分技术的提升和优化。

![image-20220309192701961](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309192701961.png)

### 2.3 字体图标的下载

-   icomoon 字库 http://icomoon.io 推荐指数 ★★★★★

IcoMoon 成立于 2011 年，推出了第一个自定义图标字体生成器，它允许用户选择所需要的图标，使它们成一字型。该字库内容种类繁多，非常全面，唯一的遗憾是国外服务器，打开网速较慢。

-   阿里 iconfont 字库 http://www.iconfont.cn/ 推荐指数 ★★★★★

这个是阿里 M2UX 的一个 iconfont 字体图标字库，包含了淘宝图标库和阿里图标库。可以使用 AI 制作图标上传生成。 重点是，免费！

-   Font Awesome[https://fa5.dashgame.com/#/](https://fa5.dashgame.com/#/)推荐指数 ★★★★★

Font Awesome 已经发展到拥有 5000 多个图标，并持续添加最受欢迎和最迫切需要的图标。不用再没有头绪的寻找你需要的图标，也不用自己拼凑，更不用从不知名的角落里寻找品牌商标。使用也及其简单，只需要引入样式文件即可直接使用

### 2.4 字体文件格式

不同浏览器所支持的字体格式是不一样的，字体图标之所以兼容，就是因为包含了主流浏览器支持的字体文件。

1. TureType**(.ttf)**格式.ttf 字体是 Windows 和 Mac 的最常见的字体，支持这种字体的浏览器有 IE9+、Firefox3.5+、
   Chrome4+、Safari3+、Opera10+、iOS Mobile、Safari4.2+；
2. Web Open Font Format**(.woff)**格式 woff 字体，支持这种字体的浏览器有 IE9+、Firefox3.5+、Chrome6+、Safari3.6+、Opera11.1+；
3. Embedded Open Type**(.eot)**格式.eot 字体是 IE 专用字体，支持这种字体的浏览器有 IE4+；
4. SVG**(.svg)**格式.svg 字体是基于 SVG 字体渲染的一种格式，支持这种字体的浏览器有 Chrome4+、Safari3.1+、Opera10.0+、iOS Mobile Safari3.2+；

### 2.5 字体图标的引入

这里介绍**icomoon 字体图标**的引入

下载完毕之后，注意原先的文件不要删，后面会用。

1. 把下载包里面的 fonts 文件夹放入页面根目录下

![image-20220309211333912](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309211333912.png)

2. 在 CSS 样式中全局声明字体： 简单理解把这些字体文件通过 css 引入到我们页面中。
   一定注意字体文件路径的问题。

```html
@font-face { font-family: 'icomoon'; src: url('fonts/icomoon.eot?7kkyc2'); src:
url('fonts/icomoon.eot?7kkyc2#iefix') format('embedded-opentype'),
url('fonts/icomoon.ttf?7kkyc2') format('truetype'),
url('fonts/icomoon.woff?7kkyc2') format('woff'),
url('fonts/icomoon.svg?7kkyc2#icomoon') format('svg'); font-weight: normal;
font-style: normal; }
```

**注**：**这里代码这可直接到下载的文件的 style.css 中粘贴**

3. html 标签内添加小图标。

这里得到图表的代码，

![image-20220309211656503](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309211656503.png)

```
<span>"\e902"</span>
```

4. 给标签定义字体。

```html
span { font-family: "icomoon"; }
```

务必保证 这个字体和上面@font-face 里面的字体保持一致

![image-20220309211927541](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309211927541.png)

### 2.6 字体图标的追加

如果工作中，原来的字体图标不够用了，我们需要添加新的字体图标到原来的字体文件中。
把压缩包里面的 `selection.json` 从新上传，然后选中自己想要新的图标，从新下载压缩包，并替换原来的文件即可。

![image-20220309212631656](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309212631656.png)

## 三. CSS 三角

### 3.1 等腰直角三角形

网页中常见一些三角形，使用 CSS 直接画出来就可以，不必做成图片或者字体图标。

原理就是将宽度和高度设置为 0.然后边框，就会生成下图的形状，**如果只需要一个三角形**，那么就把其他边框变成透明，设置一个边框，如下面 box1 所示

![image-20220309213403006](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309213403006.png)

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>CSS 三角制作</title>
    <style>
		/*上面的四彩正方形*/
        .box1 {
            width: 0;
            height: 0;
            /* border: 10px solid pink; */
            border-top: 50px solid pink;
            border-right: 50px solid red;
            border-bottom: 50px solid blue;
            border-left: 50px solid green;
        }
		/*三角形*/
        .box2 {
            width: 0;
            height: 0;
            border: 50px solid transparent;
            border-left-color: pink;
            margin: 100px auto;
        }

		/*京东代码*/
        .jd {
            position: relative;
            width: 120px;
            height: 249px;
            background-color: pink;
        }
        .jd span {
            position: absolute;
            right: 15px;
            top: -10px;
            width: 0;
            height: 0;
            /* 为了照顾兼容性 */
            line-height: 0;
            font-size: 0;
            border: 5px solid transparent;
            border-bottom-color: pink;
        }
    </style>
</head>
<body>
    <div class="box1"></div>
    <div class="box2"></div>
    <div class="jd">
        <span></span>
    </div>
</body>
</html>
```

如上面代码 box2 的三角形

![image-20220309213729575](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309213729575.png)

京东样式代码

![image-20220309213830908](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309213830908.png)

### 3.2 直角三角形（不等腰）

```
.box1 {
            width: 0;
            height: 0;
            /* 把上边框宽度调大 */
            border-top: 100px solid transparent;
            border-right: 50px solid skyblue;
            /* 左边和下边的边框宽度设置为0，或者直接不设置 */
            border-bottom: 0 solid transparent;
            border-left: 0 solid transparent;
}

也可以连写

.box1 {
     /* 1.只保留右边的边框有颜色 */
     border-color: transparent red transparent transparent;
     /* 2. 样式都是solid */
     border-style: solid;
     /* 3. 上边框宽度要大， 右边框 宽度稍小， 其余的边框该为 0 */
      border-width: 100px 50px 0 0 ;
}


```

### 3.3 京东价格图

![image-20220309220815682](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309220815682.png)

**关键代码**：

```
width: 0;
height: 0;
border-color: transparent red transparent transparent;
border-style: solid;
border-width: 22px 8px 0 0;
```

**全部代码**：

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <meta http-equiv="X-UA-Compatible" content="ie=edge" />
        <title>CSS三角强化的巧妙运用</title>
        <style>
            .price {
                width: 160px;
                height: 24px;
                line-height: 24px;
                border: 1px solid red;
                margin: 0 auto;
            }
            .miaosha {
                position: relative;
                float: left;
                width: 90px;
                height: 100%;
                background-color: red;
                text-align: center;
                color: #fff;
                font-weight: 700;
                margin-right: 8px;
            }
            .miaosha i {
                position: absolute;
                right: 0;
                top: 0;
                width: 0;
                height: 0;
                border-color: transparent #fff transparent transparent;
                border-style: solid;
                border-width: 24px 10px 0 0;
            }
            .origin {
                font-size: 12px;
                color: gray;
                text-decoration: line-through;
            }
        </style>
    </head>
    <body>
        <div class="price">
            <span class="miaosha">
                ¥1650
                <i></i>
            </span>
            <span class="origin">¥5650</span>
        </div>
    </body>
</html>
```

## 四. CSS 用户界面样式

所谓的界面样式，就是更改一些用户操作样式，以便提高更好的用户体验。

-   更改用户的鼠标样式
-   表单轮廓
-   防止表单域拖拽

### 4.1 鼠标样式 cursor

```
li {cursor: pointer; }
```

置或检索在对象上移动的鼠标指针采用何种系统预定义的光标形状。

| 属性值      | 描述     |
| ----------- | -------- |
| default     | 小白默认 |
| pointer     | 小手     |
| move        | 移动     |
| text        | 禁止     |
| not-allowed | 禁止     |

### 4.2 轮廓线

给表单添加 outline: 0; 或者 outline: none; 样式之后，就可以去掉默认的蓝色边框。

```
input {outline: none; }
```

### 4.3 防止拖拽文本域 resize

实际开发中，我们文本域右下角是不可以拖拽的。不然会影响一些布局

```
textarea{ resize: none;}
```

## 五. vertical-align 属性应用

### 5.1 使用场景

CSS 的 vertical-align 属性使用场景： 经常用于设置图片或者表单(行内块元素）和文字垂直对齐。
官方解释： 用于设置一个元素的垂直对齐方式，但是它只针对于行内元素或者行内块元素有效。

语法：

```
vertical-align : baseline | top | middle | bottom
```

| 值       | 描述                                     |
| -------- | ---------------------------------------- |
| baseline | 默认。元素放置在父元素的基线上。         |
| top      | 把元素的顶端与行中最高元素的顶端对齐     |
| middle   | 把此元素放置在父元素的中部。             |
| bottom   | 把元素的顶端与行中最低的元素的顶端对齐。 |

![image-20211119224239298](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20211119224239298.png)

### 5.2 图片、表单和文字对齐

图片、表单都属于行内块元素，默认的 vertical-align 是基线对齐。

![image-20220309214414406](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309214414406.png)

此时可以给图片、表单这些行内块元素的 vertical-align 属性设置为 middle 就可以让文字和图片垂直居中对齐了。

### 5.3 解决图片底部默认空白缝隙问题

bug：图片底侧会有一个空白缝隙，原因是行内块元素会和文字的基线对齐。
主要解决方法有两种：

1. 给图片添加 vertical-align:middle | top| bottom 等。 （提倡使用的）
2. 把图片转换为块级元素 display: block;

![image-20220309214520332](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309214520332.png)

## 六. 溢出的文字省略号显示

### 6.1 单行文本溢出显示省略号

![image-20220309214616289](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309214616289.png)

单行文本溢出显示省略号--必须满足三个条件

```html
/*1. 先强制一行内显示文本*/ white-space: nowrap; （ 默认 normal 自动换行） /*2.
超出的部分隐藏*/ overflow: hidden; /*3. 文字用省略号替代超出的部分*/
text-overflow: ellipsis;
```

### 6.2 多行文本溢出显示省略号

多行文本溢出显示省略号，有较大兼容性问题， 适合于 webKit 浏览器或移动端（移动端大部分是 webkit 内核）推荐后端人员来做。

![image-20220309214647802](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309214647802.png)

```html
overflow: hidden; text-overflow: ellipsis; /* 弹性伸缩盒子模型显示 */ display:
-webkit-box; /* 限制在一个块元素显示的文本的行数 */ -webkit-line-clamp: 2; /*
设置或检索伸缩盒对象的子元素的排列方式 */ -webkit-box-orient: vertical;
```

## 七. 常见布局技巧

### 7.1 margin 负值运用

加边框的时候会有中间两个盒子边框合并的问题：**1px+1px=2px**

![image-20211120091201027](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20211120091201027.png)

![image-20220309214828022](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309214828022.png)

1. 让每个盒子 margin 往左侧移动 -1px 正好压住相邻盒子边框
2. 鼠标经过某个盒子的时候，提高当前盒子的层级即可（如果没有有定位，则加相对定位（保留位置），如果有定位，则加 z-index）

这里建议使用**margin-right**

```
 <style>
        /* * {
            margin: 0;
            padding: 0;
        } */
        ul li {
            position: relative;/*如果没有可让鼠标经过加相对定位，否则提高层级
            float: left;
            list-style: none;
            width: 150px;
            height: 200px;
            border: 1px solid red;
            margin-right:-1px;
        }

        /* ul li:hover {
           1. 如果盒子没有定位，则鼠标经过添加相对定位即可
        position: relative;
        border: 1px solid blue;

       } */
        ul li:hover {
            /* 2.如果li都有定位，则利用 z-index提高层级 */
            z-index: 1;
            border: 1px solid blue;
        }
    </style>
```

### 7.2 文字围绕浮动元素

![image-20211120093840597](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20211120093840597.png)

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <meta http-equiv="X-UA-Compatible" content="ie=edge" />
        <title>文字围绕浮动元素的妙用</title>
        <style>
            * {
                margin: 0;
                padding: 0;
            }
            .box {
                width: 300px;
                height: 70px;
                background-color: pink;
                margin: 0 auto;
                padding: 5px;
            }
            .pic {
                float: left;
                width: 120px;
                height: 60px;
                margin-right: 5px;
            }
            .pic img {
                width: 100%;
            }
        </style>
    </head>
    <body>
        <div class="box">
            <div class="pic">
                <img src="images/img.png" alt="" />
            </div>
            <p>【集锦】热身赛-巴西0-1秘鲁 内马尔替补两人血染赛场</p>
        </div>
    </body>
</html>
```

### 7.3 行内块巧妙运用

![image-20220309215210607](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/web/image-20220309215210607.png)

页码在页面中间显示:

1. 把这些链接盒子转换为行内块， 之后给父级指定 text-align:center;
2. 利用行内块元素中间有缝隙，并且给父级添加 text-align:center; 行内块元素会水平会居中

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <meta http-equiv="X-UA-Compatible" content="ie=edge" />
        <title>行内块的巧妙运用</title>
        <style>
            * {
                margin: 0;
                padding: 0;
            }
            .box {
                /* text-align: center; */
            }
            .box a {
                display: inline-block;
                width: 36px;
                height: 36px;
                background-color: #f7f7f7;
                border: 1px solid #ccc;
                text-align: center;
                line-height: 36px;
                text-decoration: none;
                color: #333;
                font-size: 14px;
            }
            .box .prev,
            .box .next {
                width: 85px;
            }
            .box .current,
            .box .elp {
                background-color: #fff;
                border: none;
            }
            .box input {
                height: 36px;
                width: 45px;
                border: 1px solid #ccc;
                outline: none;
            }
            .box button {
                width: 60px;
                height: 36px;
                background-color: #f7f7f7;
                border: 1px solid #ccc;
            }
        </style>
    </head>
    <body>
        <div class="box">
            <a href="#" class="prev">&lt;&lt;上一页</a>
            <a href="#" class="current">2</a>
            <a href="#">3</a>
            <a href="#">4</a>
            <a href="#">5</a>
            <a href="#">6</a>
            <a href="#" class="elp">...</a>
            <a href="#" class="next">&gt;&gt;下一页</a>
            到第
            <input type="text" />
            页
            <button>确定</button>
        </div>
    </body>
</html>
```

## 八. CSS 页面初始化

不同浏览器对有些标签的默认值是不同的，为了消除不同浏览器对 HTML 文本呈现的差异，照顾浏览器的兼容，我们需要对 CSS 初始化
简单理解： CSS 初始化是指重设浏览器的样式。 (也称为 CSS reset）
每个网页都必须首先进行 CSS 初始化。
这里我们以 京东 CSS 初始化代码为例。
**Unicode 编码字体**：
把中文字体的名称用相应的 Unicode 编码来代替，这样就可以有效的避免浏览器解释 CSS 代码时候出现乱码的问题。
比如：

-   黑体 \9ED1\4F53
-   宋体 \5B8B\4F53
-   微软雅黑 \5FAE\8F6F\96C5\9ED1

```css
/* 把我们所有标签的内外边距清零 */
* {
    margin: 0;
    padding: 0;
}
/* em 和 i 斜体的文字不倾斜 */
em,
i {
    font-style: normal;
}
/* 去掉li 的小圆点 */
li {
    list-style: none;
}

img {
    /* border 0 照顾低版本浏览器 如果 图片外面包含了链接会有边框的问题 */
    border: 0;
    /* 取消图片底侧有空白缝隙的问题 */
    vertical-align: middle;
}

button {
    /* 当我们鼠标经过button 按钮的时候，鼠标变成小手 */
    cursor: pointer;
}

a {
    color: #666;
    text-decoration: none;
}

a:hover {
    color: #c81623;
}

button,
input {
    /* "\5B8B\4F53" 就是宋体的意思 这样浏览器兼容性比较好 */
    font-family: Microsoft YaHei, Heiti SC, tahoma, arial, Hiragino Sans GB, '\5B8B\4F53',
        sans-serif;
}

body {
    /* CSS3 抗锯齿形 让文字显示的更加清晰 */
    -webkit-font-smoothing: antialiased;
    background-color: #fff;
    font: 12px/1.5 Microsoft YaHei, Heiti SC, tahoma, arial, Hiragino Sans GB, '\5B8B\4F53',
        sans-serif;
    color: #666;
}

.hide,
.none {
    display: none;
}
/* 清除浮动 */
.clearfix:after {
    visibility: hidden;
    clear: both;
    display: block;
    content: '.';
    height: 0;
}

.clearfix {
    *zoom: 1;
}
```
