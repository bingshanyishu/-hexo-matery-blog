---
title: 如何在hexo博客中在线阅读pdf
author: Breezs
coverImg: /medias/banner/1.jpg
top: true
cover: false
toc: true
mathjax: false
tags:
    - pdf
    - 博客
categories:
    - 项目之树
reprintPolicy: cc_by
date: 2022-03-08 17:38:40
summary:
abbrlink: 202203081740
img: /medias/posts/11.jpg
password:
---

## 前言

## 前言

> **我这里是 matery 主题，其他主题的可参照相应思路进行修改**

有一些资料或者笔记是 pdf 版本的，如果想要放在博客中进行阅读，那么就得将其转换为 markdown 格式或者 html 格式。但是这样转换后，其原 pdf 的格式就会混乱了，排版将会变得很困难，不过一山更比一山高，由 mozilla 支持的[在线 pdf 阅读插件](https://mozilla.github.io/pdf.js/)就可让我们在网页中进行 pdf 的阅读。
![](https://img-blog.csdnimg.cn/0e53c336c12447cea6fda93ab7f4159c.png#pic_center)
**这是官方的示例**
![](https://img-blog.csdnimg.cn/d12f6eb2831c43a3aeb9a70c541dc0e9.png)
那么我们该怎么使用呢？

## 下载

要使用那么最基础的就是我们要先下载，直接去官网[在线 pdf 阅读插件](https://mozilla.github.io/pdf.js/)下载官方已经压缩好的即可。
如果去 github 下载源码还需要进行一些小操作。想挑战一下的可以去[gihub 地址](https://github.com/mozilla/pdf.js)跟着说明文档进行操作。这里我直接介绍去官网下载的。
**进入官网，点击 Download**
![](https://img-blog.csdnimg.cn/2d419f2be1894ba8a0206bcd7afb4197.png)
点击左边那个 Stable 就可以下载了
![](https://img-blog.csdnimg.cn/6d52e191725345d69d316717a88a85eb.png)

## 使用

（1）将下载到的文件解压，为了引入博客中方便直接将解压后的文件名`pdfjs-2.13.216-dist`改名为`pdfjs`。
我们得到这样一个结构的文件，在该目录中创建一个**文件夹**，命名为**data**用于**保存 pdf 文件**。

```
├── build/
│   ├── pdf.js                             - display layer
│   ├── pdf.js.map                         - display layer's source map
│   ├── pdf.worker.js                      - core layer
│   └── pdf.worker.js.map                  - core layer's source map
├── web/
│   ├── cmaps/                             - character maps (required by core)
│   ├── compressed.tracemonkey-pldi-09.pdf - PDF file for testing purposes
│   ├── debugger.js                        - helpful debugging features
│   ├── images/                            - images for the viewer and annotation icons
│   ├── locale/                            - translation files
│   ├── viewer.css                         - viewer style sheet
│   ├── viewer.html                        - viewer layout
│   ├── viewer.js                          - viewer layer
│   └── viewer.js.map                      - viewer layer's source map
|——data/                                     -这是新建的data文件，用于保存pdf资源
└── LICENSE
```

（2）然后将其放入到**博客根文件下的 resouce**中，如下图所示，**注意路径，不是主题文件的 resouce**
![](https://img-blog.csdnimg.cn/d9813eee861b4c7098a43787e19b9750.png)

（3）再在该路径下新建一个文件夹叫做**pdf**，pdf 文件夹中新建 index.md 文件填入，日期随便填都可以

```
---
title: pdf
date: 2022-03-03 16:40:27
type: "pdf"
layout: "pdf"
---
```

（4）在主题文件的 layout 文件`D:\HexoBlog\themes\hexo-theme-matery\layout`中新建一个 pdf.ejs 文件，这里作为 pdf 的一级页面，可描述多个 pdf 文件，当点击后就会进入相应文件的 pdf 阅读器中
![](https://img-blog.csdnimg.cn/adbbb795d1e64f57bfa458f9b3a9e644.png)
在该 pdf.ejs 中添加以下代码

```
<%- partial('_partial/bg-cover') %>

<style>

li {
    list-style: none;
}
.about {
    color: rgba(56, 51, 51, 0.6) !important;
    font-size: 3vw;
    text-align: center;
    font-family: 'Font Awesome 5 Free';
    font-weight: 700;
    line-height: 3vw;

}
.ul {
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 1200px;
    /* 对齐 */
    margin: 0 auto !important;
}

.list {
    position: relative;
    margin-bottom: 10px;
    color: rgba(0, 150, 250, 0.6) !important;
    background-color: rgba(255, 255, 255,0.7);
    text-align: center;
    box-shadow: 2px 2px 2px rgba(255, 255, 255,0.7);
}

.list:hover {
    transform: scale(1.02,1.02);
    transition: all 0.5s;
}

.list::before {
    position: absolute;
    left: 1rem;
    top: 1rem;
    content: '📖';
    transform: scale(2);

}
.list a .title {
    margin: 0;
    height: 4rem;
    font-size: 3rem !important;
    border-bottom: 2px solid #fff;
    color: rgba(0, 150, 250, 0.6) !important;
    line-height: 4rem;
}

.list a .explain {
    margin: 0;
    text-align: left;
    white-space:normal;
    line-height: 3vw;
    color: rgba(0, 150, 250, 0.6) !important;
    font-size: 1.8vw !important;
}


/* 手机端字体 */
@media only screen and (max-width: 601px) {
    .list a .title {
        font-size: 2.2rem !important;
    }
    .list::before {
        content: '📖';
        transform: scale(1.5);
    }
    .about {
        font-size: 4vw;
        line-height: 4.5vw;

}
}

</style>

<main class="centent">
    <h2 class="about">这儿是一些基于pdfjs进行阅读的书籍或者笔记！<br><em>注意：阅读请关闭IDM</em></h2>
    <ul class="ul">
        <li class="list">
            <a href="/pdfjs/web/viewer.html?file=../data/css揭秘.pdf" target="_Blank">
                <h3 class="title">《css揭秘》</h3>
                <p class="explain">这本书是为新一代 CSS 所写的新一代 CSS 图书。也许从前的 CSS 只会让你联想到浏览器里的各种
                    小把戏，但如今 CSS 已经成为一门功能强大、具备完整生态、涉及 80 多项 W3C 规范的复杂语言。在我
                    所知的技术专家中，没人比 Lea Verou 更能领会新一代 CSS 的精髓，没人能像她那样透彻地给出问题解决之道
                </p>
            </a>
        </li>
    </ul>

</main>
```

**注意：以后 pdf 的介绍就放在 li 标签里面，参考第一个小 li 进行修改**

（5）接着在博客根目录下的配置文件`_config.yml`中取消对 pdfjs 的渲染
![](https://img-blog.csdnimg.cn/544490e80f9c49c79a404220c812e091.png)

（6）最后在主题配置文件`D:\HexoBlog\themes\hexo-theme-matery\_config.yml`中添加导航，我这里添加在 Archives 中作为二级导航。

```
Archives:
    icon: fas fa-archive
    children:
      - name: 时轴
        url: /archives
        icon: fas fa-hourglass-half
      - name: 分类
        url: /categories
        icon: fas fa-bookmark
      - name: 标签
        url: /tags
        icon: fas fa-tag
      - name: PDF
        url: /pdf
        icon: fas fa-file-pdf
```

![](https://img-blog.csdnimg.cn/bc7b564f4fa948229bd74f12bac7fd7c.png)
