---
title: Ajax概述，封装以及联合模板引擎进行数据交互
author: Breezs
coverImg: /medias/banner/1.jpg
top: false
cover: false
toc: true
mathjax: false
tags:
    - Ajax
    - 前端
categories:
    - 技能之树
reprintPolicy: cc_by
img: /medias/posts/10.jpg
date: 2022-03-19 22:48:51
abbrlink: 202203192248，
summary: 网速慢的情况下，页面加载时间长，用户只能等待，于是Ajax诞生了，它是浏览器提供的一套方法，可以实现页面无刷新更新数据，提高用户浏览网站应用的体验。
password:
---

# Ajax 概述，封装以及联合模板引擎进行数据交互

博客园主页：[博客园主页-冰山一树 Sankey](https://www.cnblogs.com/breezs)
CSDN 主页：[CSDN 主页-冰山一树 Sankey](https://blog.csdn.net/m0_59464010)

更多资料可参考[Ajax 介绍篇丨慕课网教程 (imooc.com)](https://www.imooc.com/wiki/ajaxlesson/ajaxintro.html)

## 一. Ajax 概述

在网站中存在以下问题：

-   网速慢的情况下，页面加载时间长，用户只能等待
-   表单提交后，如果一项内容不合格，需要重新填写所有表单内容
-   页面跳转，重新加载页面，造成资源浪费，增加用户等待时间

于是 Ajax 诞生了，Ajax：标准读音 [ˈeɪˌdʒæks] ，中文音译：阿贾克斯

它是浏览器提供的一套方法，可以实现页面无刷新更新数据，提高用户浏览网站应用的体验。

![录制_2022_03_17_21_37_32_165](https://img-blog.csdnimg.cn/img_convert/80675063efb818dbb868bdca7970be34.gif)

## 二. Ajax 运行环境及实现

### 2.1 Ajax 运行环境

Ajax 相当于浏览器发送请求与接收响应的代理人，以实现在不影响用户浏览页面的情况下，局部更新页面数据，从而提高用户体验。在浏览器端与服务器端进行请求响应是不可以控制的，但使用 Ajax 后，开发人员人员可控制其过程。

![image-20220317223015626](https://img-blog.csdnimg.cn/img_convert/fc8205566ed1f3dc90955086e710ea0e.png)

那如何实现 Ajax 呢？

1. 创建 Ajax 对象

```
var xhr = new XMLHttpRequest();
```

2. 告诉 Ajax 请求地址以及请求方式

```
xhr.open('get', 'http://www.example.com');
```

3. 发送请求

```
xhr.send();
```

4. 获取服务器端给与客户端的响应数据

```
xhr.onload = function () {
     console.log(xhr.responseText);
 }
```

**因为 Ajax 技术需要运行在网站环境中才能生效，下面使用 Node 创建的服务器作为网站服务器。**

手写在创建一个文件夹 server，在其根目录下再创建 public，使用 npm 安装**express 和 body-parser**，其**package.jion**文件如下

```json
{
    "name": "code",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "author": "",
    "license": "ISC",
    "dependencies": {
        "body-parser": "^1.18.3",
        "express": "^4.16.4"
    }
}
```

然后再在根目录下创建**app.js**文件，这里编写服务端代码

### 2.2 传递 get 请求参数

在 public 中新建`传递get请求参数.html`文件

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
    </head>
    <body>
        <p>
            <input type="text" id="username" />
        </p>
        <p>
            <input type="text" id="age" />
        </p>
        <p>
            <input type="button" value="提交" id="btn" />
        </p>
        <script type="text/javascript">
            // 获取按钮元素
            var btn = document.getElementById('btn');
            // 获取姓名文本框
            var username = document.getElementById('username');
            // 获取年龄文本框
            var age = document.getElementById('age');
            // 为按钮添加点击事件
            btn.onclick = function () {
                // 创建ajax对象
                var xhr = new XMLHttpRequest();
                // 获取用户在文本框中输入的值
                var nameValue = username.value;
                var ageValue = age.value;
                // 拼接请求参数
                var params = 'username=' + nameValue + '&age=' + ageValue;
                // 配置ajax对象
                xhr.open('get', 'http://localhost:3000/get?' + params);
                // 发送请求
                xhr.send();
                // 获取服务器端响应的数据
                xhr.onload = function () {
                    console.log(xhr.responseText);
                };
            };
        </script>
    </body>
</html>
```

在服务的`app.js`，添加

```javascript
// 引入express框架
const express = require('express');
// 路径处理模块
const path = require('path');
const bodyParser = require('body-parser');
const fs = require('fs');
// 创建web服务器
const app = express();

// 静态资源访问服务功能
app.use(express.static(path.join(__dirname, 'public')));

// 传递get请求参数
app.get('/get', (req, res) => {
    //req.query得到json字符串
    res.send(req.query);
});
```

```javascript
这里放在app.js的最后，
// 监听端口
app.listen(3000);
// 控制台提示输出
console.log('服务器启动成功');
```

在 server 下调用命令行启动 nodejs 服务器，为了方便调试，可使用

```javascript
nodemon app.js
```

然后在浏览器打开`http://localhost:4000/传递get请求参数.html`,输入数据后，可返回输入值。

**解释下这里的过程**： 用 get 的请求方法把输入的数据从浏览器端**发送**到服务端，服务端再把得到的数据再**返回**到浏览器端进行输出，当然这里为了测试，从服务端发送到浏览器端的数据也可以是**其他内容**

![image-20220317231137737](https://img-blog.csdnimg.cn/img_convert/c88ff9df3cc6b2a43547995815d441b0.png)

可以看到这里的请求的 url 是域名+`?key=value&key=value`的形式以及请求方法为`get`

![image-20220317231737308](https://img-blog.csdnimg.cn/img_convert/cf4aeb03cc97c0bc755f9467a3aa0c64.png)

### 2.3 传递 post 请求参数

传递 post 请求参数有两种方式，第一种格式和 get 相同，传递的数据格式为`key=value&key=value`

在 public 中新建`传递post请求参数.html`文件

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
    </head>
    <body>
        <p>
            <input type="text" id="username" />
        </p>
        <p>
            <input type="text" id="age" />
        </p>
        <p>
            <input type="button" value="提交" id="btn" />
        </p>
        <script type="text/javascript">
            // 获取按钮元素
            var btn = document.getElementById('btn');
            // 获取姓名文本框
            var username = document.getElementById('username');
            // 获取年龄文本框
            var age = document.getElementById('age');
            // 为按钮添加点击事件
            btn.onclick = function () {
                // 创建ajax对象
                var xhr = new XMLHttpRequest();
                // 获取用户在文本框中输入的值
                var nameValue = username.value;
                var ageValue = age.value;
                // 拼接请求参数
                var params = 'username=' + nameValue + '&age=' + ageValue;
                // 配置ajax对象
                xhr.open('post', 'http://localhost:3000/post');
                // 设置请求参数格式的类型（post请求必须要设置）
                xhr.setRequestHeader(
                    'Content-Type',
                    'application/x-www-form-urlencoded'
                );
                // 发送请求
                xhr.send(params);
                // 获取服务器端响应的数据
                xhr.onload = function () {
                    console.log(xhr.responseText);
                };
            };
        </script>
    </body>
</html>
```

在原 app.js 的基础上再添加

```javascript
//解析传递的post数据，格式为
const bodyParser = require('body-parser');
app.use(bodyParser.urlencoded());
// 传递post请求参数
app.post('/post', (req, res) => {
    res.send(req.body);
});
```

打开浏览器中输入`http://localhost:3000/post请求参数.html`, 打开浏览器调试，点击网络，输入数据后，可以得到 post，请求 url 以及请求方法

![image-20220318153531163](https://img-blog.csdnimg.cn/img_convert/2ccfae16a35c92a21c303b16ca7075bd.png)

这里的表单数据为输入的值，说明数据传递成功。

![image-20220318153805465](https://img-blog.csdnimg.cn/img_convert/5e861476b16d5634f219ae7e393e638f.png)

第二种传递的格式为 json 数据，主要区别在于`xhr.setRequestHeader('Content-Type', 'application/json');`，以及服务端的 app.use(bodyParser.json());具体看下面的代码

> 注意：get 请求是不能提交 json 对象数据格式的，传统网站的表单提交也是不支持 json 对象数据格式的。

在 public 中新建`向服务器端传递JSON格式的请求参数.html`文件

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<script type="text/javascript">
		// 1.创建ajax对象
		var xhr = new XMLHttpRequest();
		// 2.告诉Ajax对象要向哪发送请求，以什么方式发送请求
		// 1)请求方式 2)请求地址
		xhr.open('post', 'http://localhost:3000/json');
		// 通过请求头告诉服务器端客户端向服务器端传递的请求参数的格式是什么
		xhr.setRequestHeader('Content-Type', 'application/json');
		// JSON.stringify() 将json对象转换为json字符串
		// 3.发送请求
		xhr.send(JSON.stringify({name: 'lisi', age:50}));
		// 4.获取服务器端响应到客户端的数据
        xhr.onload = function () {
            console.log(xhr.responseText)
        }
	</script>
</body>
</html>
```

在原 app.js 的基础上再添加

```javascript
//将app.use(bodyParser.urlencoded())改为app.use(bodyParser.json());
app.use(bodyParser.json());
//向服务器端传递JSON格式的请求参数
app.post('/json', (req, res) => {
    res.send(req.body);
});
```

注意：还需要将`app.use(bodyParser.urlencoded());`改为`app.use(bodyParser.json());`

### 2.5 获取服务端响应

在说明之前，先来介绍一个概念——报文

在 HTTP 请求和响应的过程中传递的数据块就叫报文，包括要传送的数据和一些附加信息，这些数据和信息要遵守规定好的格式。

![image-20220318154706440](https://img-blog.csdnimg.cn/img_convert/6fb3335feed4271849bc3b4dc674b274.png)

上面的 get 与 post 请求，我们均是使用 onload 来获取服务端的报文，但也可以通过另外的方法来获取：

在创建 ajax 对象，配置 ajax 对象，发送请求，以及接收完服务器端响应报文，这个过程中的每一个步骤都会对应一个数值，这个数值就是 ajax 状态码。使用**onreadystatechange** **事件**，可以检测状态码的变化，当状态码为 4 时就可以通过 xhr.responseText 获取服务器端的响应数据。

```
0：请求未初始化(还没有调用open())
1：请求已经建立，但是还没有发送(还没有调用send())
2：请求已经发送
3：请求正在处理中，通常响应中已经有部分数据可以用了
4：响应已经完成，可以获取并使用服务器的响应了
```

即下面方法可 onload 方法等效

```javascript
// 当Ajax状态码发生变化时
xhr.onreadystatechange = function () {
    // 判断当Ajax状态码为4时
    if (xhr.readyState == 4) {
        // 获取服务器端的响应数据
        console.log(xhr.responseText);
    }
};
```

### 2.4 Ajax 错误处理

-   Ajax 状态码: 表示 Ajax 请求的过程状态 ajax 对象返回的
-   Http 状态码: 表示请求的处理结果 是服务器端返回的

1. 网络畅通，服务器端能接收到请求，服务器端返回的结果不是预期结果。

可以判断服务器端返回的状态码，分别进行处理。xhr.status 获取 http 状态码

2. 网络畅通，服务器端没有接收到请求，返回 404 状态码。

检查请求地址是否错误。

3. 网络畅通，服务器端能接收到请求，服务器端返回 500 状态码。

服务器端错误，找后端程序员进行沟通。

4. 网络中断，请求无法发送到服务器端。

会触发 xhr 对象下面的 onerror 事件，在 onerror 事件处理函数中对错误进行处理。

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
    </head>
    <body>
        <button id="btn">发送Ajax请求</button>
        <script type="text/javascript">
            var btn = document.getElementById('btn');

            btn.onclick = function () {
                // 1.创建ajax对象
                var xhr = new XMLHttpRequest();
                // 2.告诉Ajax对象要向哪发送请求，以什么方式发送请求
                // 1)请求方式 2)请求地址
                xhr.open('get', 'http://localhost:3000/error');
                // 3.发送请求
                xhr.send();
                // 4.获取服务器端响应到客户端的数据
                xhr.onload = function () {
                    // xhr.status 获取http状态码
                    console.log(xhr.responseText);

                    if (xhr.status == 400) {
                        alert('请求出错');
                    }
                };
                // 当网络中断时会触发onerrr事件
                xhr.onerror = function () {
                    alert('网络中断, 无法发送Ajax请求');
                };
            };

            // Ajax状态码: 表示Ajax请求的过程状态 ajax对象返回的
            // Http状态码: 表示请求的处理结果 是服务器端返回的
        </script>
    </body>
</html>
```

服务端 app.js

```
app.get('/error', (req, res) => {
	//console.log(abc);
	res.status(400).send('not ok');
});
```

## 三. Ajax 封装

发送一次请求代码过多，发送多次请求代码冗余且重复。我们可以将请求代码封装到函数中，发请求时调用函数即可。

```javascript
function ajax(options) {
    // 默认值
    var defaults = {
        type: 'get',
        url: '',
        async: true,
        data: {},
        header: {
            'Content-Type': 'application/x-www-form-urlencoded',
        },
        success: function () {},
        error: function () {},
    };
    // 使用用户传递的参数替换默认值参数
    Object.assign(defaults, options);
    // 创建ajax对象
    var xhr = new XMLHttpRequest();
    // 参数拼接变量
    var params = '';
    // 循环参数
    for (var attr in defaults.data) {
        // 参数拼接
        params += attr + '=' + defaults.data[attr] + '&';
        // 去掉参数中最后一个&
        params = params.substr(0, params.length - 1);
    }
    // 如果请求方式为get
    if (defaults.type == 'get') {
        // 将参数拼接在url地址的后面
        defaults.url += '?' + params;
    }

    // 配置ajax请求
    xhr.open(defaults.type, defaults.url, defaults.async);
    // 如果请求方式为post
    if (defaults.type == 'post') {
        // 设置请求头
        xhr.setRequestHeader('Content-Type', defaults.header['Content-Type']);
        // 如果想服务器端传递的参数类型为json
        if (defaults.header['Content-Type'] == 'application/json') {
            // 将json对象转换为json字符串
            xhr.send(JSON.stringify(defaults.data));
        } else {
            // 发送请求
            xhr.send(params);
        }
    } else {
        xhr.send();
    }
    // 请求加载完成
    xhr.onload = function () {
        // 获取服务器端返回数据的类型
        var contentType = xhr.getResponseHeader('content-type');
        // 获取服务器端返回的响应数据
        var responseText = xhr.responseText;
        // 如果服务器端返回的数据是json数据类型
        if (contentType.includes('application/json')) {
            // 将json字符串转换为json对象
            responseText = JSON.parse(responseText);
        }
        // 如果请求成功
        if (xhr.status == 200) {
            // 调用成功回调函数, 并且将服务器端返回的结果传递给成功回调函数
            defaults.success(responseText, xhr);
        } else {
            // 调用失败回调函数并且将xhr对象传递给回调函数
            defaults.error(responseText, xhr);
        }
    };
    // 当网络中断时
    xhr.onerror = function () {
        // 调用失败回调函数并且将xhr对象传递给回调函数
        defaults.error(xhr);
    };
}
```

## 四. 模板引擎

### 4.1 下载

使用模板引擎提供的模板语法，可以将数据和 HTML 拼接起来。官方地址： https://aui.github.io/art-template/zh-cn/index.html

先去下载 art-template 文件

进入官网，点击 Docs

![image-20220318160106408](https://img-blog.csdnimg.cn/img_convert/fb6638afeda9748d9c592452e69aacdd.png)

然后点击**安装**，将 temlate-web.js 另存到本地就下载好了

![image-20220318160147295](https://img-blog.csdnimg.cn/img_convert/2e7b9d0a0376ea6f1f06890af432f812.png)

### 4.2 使用步骤

1. 下载 art-template 模板引擎库文件并在 HTML 页面中引入库文件

```
<script src="./js/template-web.js"></script>
```

2. 准备 art-template 模板

```
<script id="tpl" type="text/html">
     <div class="box"></div>
 </script>
```

3. 告诉模板引擎将哪一个模板和哪个数据进行拼接

```
var html = template('tpl', {username: 'zhangsan', age: '20'});
```

4. 将拼接好的 html 字符串添加到页面中

```
 document.getElementById('container').innerHTML = html;
```

5. 通过模板语法告诉模板引擎，数据和 html 字符串要如何拼接

```
<script id="tpl" type="text/html">
     <div class="box"> {{ username }} </div>
 </script>
```

### 4.3 案例

下面介绍三个案例说明如何使用模板引擎，一起利用 Ajax 进行数据的交互。

所有服务端均在 app.js 中。

```javascript
// 引入express框架
const express = require('express');
// 路径处理模块
const path = require('path');
const formidable = require('formidable');
// 创建web服务器
const app = express();

// 静态资源访问服务功能
app.use(express.static(path.join(__dirname, 'public')));

// 邮箱地址验证
app.get('/verifyEmailAdress', (req, res) => {
    // 接收客户端传递过来的邮箱地址
    const email = req.query.email;
    // 判断邮箱地址注册过的情况
    if (email == 'itheima@itcast.cn') {
        // 设置http状态码并对客户端做出响应
        res.status(400).send({
            message: '邮箱地址已经注册过了, 请更换其他邮箱地址',
        });
    } else {
        // 邮箱地址可用的情况
        // 对客户端做出响应
        res.send({ message: '恭喜, 邮箱地址可用' });
    }
});

// 输入框文字提示
app.get('/searchAutoPrompt', (req, res) => {
    // 搜索关键字
    const key = req.query.key;
    // 提示文字列表
    const list = [
        '黑马程序员',
        '黑马程序员官网',
        '黑马程序员顺义校区',
        '黑马程序员学院报名系统',
        '传智播客',
        '传智博客前端与移动端开发',
        '传智播客大数据',
        '传智播客python',
        '传智播客java',
        '传智播客c++',
        '传智播客怎么样',
    ];
    // 搜索结果
    let result = list.filter((item) => item.includes(key));
    // 将查询结果返回给客户端
    res.send(result);
});

// 获取省份
app.get('/province', (req, res) => {
    res.json([
        {
            id: '001',
            name: '黑龙江省',
        },
        {
            id: '002',
            name: '四川省',
        },
        {
            id: '003',
            name: '河北省',
        },
        {
            id: '004',
            name: '江苏省',
        },
    ]);
});

// 根据省份id获取城市
app.get('/cities', (req, res) => {
    // 获取省份id
    const id = req.query.id;
    // 城市信息
    const cities = {
        '001': [
            {
                id: '300',
                name: '哈尔滨市',
            },
            {
                id: '301',
                name: '齐齐哈尔市',
            },
            {
                id: '302',
                name: '牡丹江市',
            },
            {
                id: '303',
                name: '佳木斯市',
            },
        ],
        '002': [
            {
                id: '400',
                name: '成都市',
            },
            {
                id: '401',
                name: '绵阳市',
            },
            {
                id: '402',
                name: '德阳市',
            },
            {
                id: '403',
                name: '攀枝花市',
            },
        ],
        '003': [
            {
                id: '500',
                name: '石家庄市',
            },
            {
                id: '501',
                name: '唐山市',
            },
            {
                id: '502',
                name: '秦皇岛市',
            },
            {
                id: '503',
                name: '邯郸市',
            },
        ],
        '004': [
            {
                id: '600',
                name: '常州市',
            },
            {
                id: '601',
                name: '徐州市',
            },
            {
                id: '602',
                name: '南京市',
            },
            {
                id: '603',
                name: '淮安市',
            },
        ],
    };
    // 响应
    res.send(cities[id]);
});

// 根据城市id获取县城
app.get('/areas', (req, res) => {
    // 获取城市id
    const id = req.query.id;
    // 县城信息
    const areas = {
        300: [
            {
                id: '20',
                name: '道里区',
            },
            {
                id: '21',
                name: '南岗区',
            },
            {
                id: '22',
                name: '平房区',
            },
            {
                id: '23',
                name: '松北区',
            },
        ],
        301: [
            {
                id: '30',
                name: '龙沙区',
            },
            {
                id: '31',
                name: '铁锋区',
            },
            {
                id: '32',
                name: '富拉尔基区',
            },
        ],
    };
    // 响应
    res.send(areas[id] || []);
});

// 监听端口
app.listen(3000);
// 控制台提示输出
console.log('服务器启动成功');
```

#### 4.3.1 验证邮箱地址唯一性

![验证邮箱唯一性](https://img-blog.csdnimg.cn/img_convert/aae4f2febd5a61fff47ba6b600ab9c3e.gif)

在 public 文件夹下面新建`验证邮箱地址唯一性.html`

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <title>验证邮箱地址是否已经注册</title>
        <link
            rel="stylesheet"
            href="/assets/bootstrap/dist/css/bootstrap.min.css"
        />
        <style type="text/css">
            p:not(:empty) {
                padding: 15px;
            }
            .container {
                padding-top: 100px;
            }
        </style>
    </head>
    <body>
        <div class="container">
            <div class="form-group">
                <label>邮箱地址</label>
                <input
                    type="email"
                    class="form-control"
                    placeholder="请输入邮箱地址"
                    id="email"
                />
            </div>
            <!-- 错误 bg-danger 正确 bg-success -->
            <p id="info"></p>
        </div>
        <script src="/js/ajax.js"></script>
        <script>
            // 获取页面中的元素
            var emailInp = document.getElementById('email');
            var info = document.getElementById('info');

            // 当文本框离开焦点以后
            emailInp.onblur = function () {
                // 获取用户输入的邮箱地址
                var email = this.value;
                // 验证邮箱地址的正则表达式
                var reg =
                    /^[A-Za-z\d]+([-_.][A-Za-z\d]+)*@([A-Za-z\d]+[-.])+[A-Za-z\d]{2,4}$/;
                // 如果用户输入的邮箱地址不符合规则
                if (!reg.test(email)) {
                    // 给出用户提示
                    info.innerHTML = '请输入符合规则的邮箱地址';
                    // 让提示信息显示为错误提示信息的样式
                    info.className = 'bg-danger';
                    // 阻止程序向下执行
                    return;
                }

                // 向服务器端发送请求
                ajax({
                    type: 'get',
                    url: 'http://localhost:3000/verifyEmailAdress',
                    data: {
                        email: email,
                    },
                    success: function (result) {
                        console.log(result);
                        info.innerHTML = result.message;
                        info.className = 'bg-success';
                    },
                    error: function (result) {
                        console.log(result);
                        info.innerHTML = result.message;
                        info.className = 'bg-danger';
                    },
                });
            };
        </script>
    </body>
</html>
```

运行 app.js，然后在浏览器中输入`http://localhost:3000/验证邮箱地址唯一性.html`

#### 4.3.2 搜索框内容自动提示

![搜索框内容自动提示](https://img-blog.csdnimg.cn/img_convert/0375d23f660d79fc5f4a3d42c20908b9.gif)

在 public 文件夹下面新建`搜索框内容自动提示.html`

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <title>搜索框输入文字自动提示</title>
        <link
            rel="stylesheet"
            href="/assets/bootstrap/dist/css/bootstrap.min.css"
        />
        <style type="text/css">
            .container {
                padding-top: 150px;
            }
            .list-group {
                display: none;
            }
        </style>
    </head>
    <body>
        <div class="container">
            <div class="form-group">
                <input
                    type="text"
                    class="form-control"
                    placeholder="请输入搜索关键字"
                    id="search"
                />
                <ul class="list-group" id="list-box"></ul>
            </div>
        </div>
        <script src="/js/ajax.js"></script>
        <script src="/js/template-web.js"></script>
        <script type="text/html" id="tpl">
            {{each result}}
            <li class="list-group-item">{{$value}}</li>
            {{/each}}
        </script>
        <script>
            // 获取搜索框
            var searchInp = document.getElementById('search');
            // 获取提示文字的存放容器
            var listBox = document.getElementById('list-box');
            // 存储定时器的变量
            var timer = null;
            // 当用户在文本框中输入的时候触发
            searchInp.oninput = function () {
                // 清除上一次开启的定时器
                clearTimeout(timer);
                // 获取用户输入的内容
                var key = this.value;
                // 如果用户没有在搜索框中输入内容
                if (key.trim().length == 0) {
                    // 将提示下拉框隐藏掉
                    listBox.style.display = 'none';
                    // 阻止程序向下执行
                    return;
                }

                // 开启定时器 让请求延迟发送
                timer = setTimeout(function () {
                    // 向服务器端发送请求
                    // 向服务器端索取和用户输入关键字相关的内容
                    ajax({
                        type: 'get',
                        url: 'http://localhost:3000/searchAutoPrompt',
                        data: {
                            key: key,
                        },
                        success: function (result) {
                            // 使用模板引擎拼接字符串
                            var html = template('tpl', { result: result });
                            // 将拼接好的字符串显示在页面中
                            listBox.innerHTML = html;
                            // 显示ul容器
                            listBox.style.display = 'block';
                        },
                    });
                }, 800);
            };
        </script>
    </body>
</html>
```

运行 app.js，然后在浏览器中输入`http://localhost:3000/搜索框内容自动提示.html`

#### 4.3.3 省市区联动

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-kLWXExa1-1647700819349)(C:/Users/27532/Desktop/省市区三级联动.gif)]

在 public 文件夹下面新建`省市区联动.html`

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <title>搜索框输入文字自动提示</title>
        <link
            rel="stylesheet"
            href="/assets/bootstrap/dist/css/bootstrap.min.css"
        />
        <style type="text/css">
            .container {
                padding-top: 150px;
            }
        </style>
    </head>
    <body>
        <div class="container">
            <div class="form-inline">
                <div class="form-group">
                    <select class="form-control" id="province"></select>
                </div>
                <div class="form-group">
                    <select class="form-control" id="city">
                        <option>请选择城市</option>
                    </select>
                </div>
                <div class="form-group">
                    <select class="form-control" id="area">
                        <option>请选择县城</option>
                    </select>
                </div>
            </div>
        </div>
        <script src="/js/ajax.js"></script>
        <script src="/js/template-web.js"></script>
        <!-- 省份模板 -->
        <script type="text/html" id="provinceTpl">
            <option>请选择省份</option>
            {{each province}}
            <option value="{{$value.id}}">{{$value.name}}</option>
            {{/each}}
        </script>
        <!-- 城市模板 -->
        <script type="text/html" id="cityTpl">
            <option>请选择城市</option>
            {{each city}}
            <option value="{{$value.id}}">{{$value.name}}</option>
            {{/each}}
        </script>
        <!-- 县城模板 -->
        <script type="text/html" id="areaTpl">
            <option>请选择县城</option>
            {{each area}}
            <option value="{{$value.id}}">{{$value.name}}</option>
            {{/each}}
        </script>
        <script>
            // 获取省市区下拉框元素
            var province = document.getElementById('province');
            var city = document.getElementById('city');
            var area = document.getElementById('area');
            // 获取省份信息
            ajax({
                type: 'get',
                url: 'http://localhost:3000/province',
                success: function (data) {
                    // 将服务器端返回的数据和html进行拼接
                    var html = template('provinceTpl', { province: data });
                    // 将拼接好的html字符串显示在页面中
                    province.innerHTML = html;
                },
            });

            // 为省份的下拉框添加值改变事件
            province.onchange = function () {
                // 获取省份id
                var pid = this.value;

                // 清空县城下拉框中的数据
                var html = template('areaTpl', { area: [] });
                area.innerHTML = html;

                // 根据省份id获取城市信息
                ajax({
                    type: 'get',
                    url: '/cities',
                    data: {
                        id: pid,
                    },
                    success: function (data) {
                        var html = template('cityTpl', { city: data });
                        city.innerHTML = html;
                    },
                });
            };

            // 当用户选择城市的时候
            city.onchange = function () {
                // 获取城市id
                var cid = this.value;
                // 根据城市id获取县城信息
                ajax({
                    type: 'get',
                    url: 'http://localhost:3000/areas',
                    data: {
                        id: cid,
                    },
                    success: function (data) {
                        var html = template('areaTpl', { area: data });
                        area.innerHTML = html;
                    },
                });
            };
        </script>
    </body>
</html>
```

运行 app.js，然后在浏览器中输入`http://localhost:3000/省市区联动.html`
