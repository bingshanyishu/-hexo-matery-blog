---
title: 如何在Ajax中使用FormData对象传递数据，$.ajax方法怎么使用
author: Sankey
coverImg: /medias/banner/1.jpg
top: false
cover: false
toc: true
mathjax: false
tags:
    - Ajax
categories:
    - 技能之树
reprintPolicy: cc_by
img: /medias/posts/11.jpg
date: 2022-03-19 22:54:35
abbrlink: 202203192254
summary:
password:
---

# 如何在 Ajax 中使用 FormData 对象传递数据，$.ajax 方法怎么使用

博客园主页：[博客园主页-冰山一树 Sankey](https://www.cnblogs.com/bingshanyishu)
CSDN 主页：[CSDN 主页-冰山一树 Sankey](https://blog.csdn.net/m0_59464010)

Ajax 基础概述以及封装请查看[ Ajax 概述，封装以及联合模板引擎进行数据交互\_冰山一树 Sankey 的博客-CSDN 博客](https://blog.csdn.net/m0_59464010/article/details/123604761)

## 一. FormData 对象

### 1.1 使用

作用：

1. 模拟 HTML 表单，相当于将 HTML 表单映射成表单对象，自动将表单对象中的数据拼接成请求参数的格式。

2. 异步上传二进制文件

3. **准备 HTML 表单**

```
<form id="form">
     <input type="text" name="username" />
     <input type="password" name="password" />
     <input type="button"/>
</form>
```

2. **将 HTML 表单转化为 formData 对象**

```
var form = document.getElementById('form');
var formData = new FormData(form);
```

3.  **提交表单对象**

```
xhr.send(formData);
```

**注意：**

1. Formdata 对象不能用于 get 请求，因为对象需要被传递到 send 方法中，而 get 请求方式的请求参数只能放在请求地址的后面。

2. 服务器端 bodyParser 模块不能解析 formData 对象表单数据，我们需要使用 formidable 模块进行解析。

具体可看下面代码

服务端 app.js 中代码

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

app.post('/formData', (req, res) => {
    // 创建formidable表单解析对象
    const form = new formidable.IncomingForm();
    // 解析客户端传递过来的FormData对象
    form.parse(req, (err, fields, files) => {
        res.send(fields);
    });
});

// 监听端口
app.listen(3000);
// 控制台提示输出
console.log('服务器启动成功');
```

浏览器端代码

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<!-- 创建普通的html表单 -->
	<form id="form">
		<input type="text" name="username">
		<input type="password" name="password">
		<input type="button" id="btn" value="提交">
	</form>
	<script type="text/javascript">
		// 获取按钮
		var btn = document.getElementById('btn');
		// 获取表单
		var form = document.getElementById('form');
		// 为按钮添加点击事件
		btn.onclick = function () {
			// 将普通的html表单转换为表单对象
			var formData = new FormData(form);
			// 创建ajax对象
			var xhr = new XMLHttpRequest();
			// 对ajax对象进行配置
			xhr.open('post', 'http://localhost:3000/formData');
			// 发送ajax请求
			xhr.send(formData);
			// 监听xhr对象下面的onload事件
			xhr.onload = function () {
				// 对象http状态码进行判断
				if (xhr.status == 200) {
					console.log(xhr.responseText);
				}
			}
		}
	</script>
</body>
</html>
```

### 1.2 实例方法

1. 获取表单对象中属性的值

```
formData.get('key');
```

2. 设置表单对象中属性的值

```
formData.set('key', 'value');
```

3. 删除表单对象中属性的值

```
formData.delete('key');
```

4. 向表单对象中追加属性值

```
formData.append('key', 'value');
```

**注意**：set 方法与 append 方法的区别是，在属性名已存在的情况下，set 会覆盖已有键名的值，append 会保留两个值。

### 1.3 实现二级制文件上传

在 public 文件夹下面新建`FormData对象实现二进制文件上传.html`，然后添加

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
        <link
            rel="stylesheet"
            href="/assets/bootstrap/dist/css/bootstrap.min.css"
        />
        <style type="text/css">
            .container {
                padding-top: 60px;
            }
            .padding {
                padding: 5px 0 20px 0;
            }
        </style>
    </head>
    <body>
        <div class="container">
            <div class="form-group">
                <label>请选择文件</label>
                <input type="file" id="file" />
                <div class="padding" id="box">
                    <!--<img src="" class="img-rounded img-responsive">-->
                </div>
                <div class="progress">
                    <div class="progress-bar" style="width: 0%;" id="bar">
                        0%
                    </div>
                </div>
            </div>
        </div>
        <script type="text/javascript">
            // 获取文件选择控件
            var file = document.getElementById('file');
            // 获取进度条元素
            var bar = document.getElementById('bar');
            // 获取图片容器
            var box = document.getElementById('box');
            // 为文件选择控件添加onchanges事件
            // 在用户选择文件时触发
            file.onchange = function () {
                // 创建空的formData表单对象
                var formData = new FormData();
                // 将用户选择的文件追加到formData表单对象中
                formData.append('attrName', this.files[0]);
                // 创建ajax对象
                var xhr = new XMLHttpRequest();
                // 对ajax对象进行配置
                xhr.open('post', 'http://localhost:3000/upload');
                // 在文件上传的过程中持续触发
                xhr.upload.onprogress = function (ev) {
                    // ev.loaded 文件已经上传了多少
                    // ev.total  上传文件的总大小
                    var result = (ev.loaded / ev.total) * 100 + '%';
                    // 设置进度条的宽度
                    bar.style.width = result;
                    // 将百分比显示在进度条中
                    bar.innerHTML = result;
                };
                // 发送ajax请求
                xhr.send(formData);
                // 监听服务器端响应给客户端的数据
                xhr.onload = function () {
                    // 如果服务器端返回的http状态码为200
                    // 说明请求是成功的
                    if (xhr.status == 200) {
                        // 将服务器端返回的数据显示在控制台中
                        var result = JSON.parse(xhr.responseText);
                        // 动态创建img标签
                        var img = document.createElement('img');
                        // 给图片标签设置src属性
                        img.src = result.path;
                        // 当图片加载完成以后
                        img.onload = function () {
                            // 将图片显示在页面中
                            box.appendChild(img);
                        };
                    }
                };
            };
        </script>
    </body>
</html>
```

服务端 app.js 代码

```js
// 引入express框架
const express = require('express');
// 路径处理模块
const path = require('path');
const formidable = require('formidable');
// 创建web服务器
const app = express();

// 静态资源访问服务功能
app.use(express.static(path.join(__dirname, 'public')));

// 实现文件上传的路由
app.post('/upload', (req, res) => {
    // 创建formidable表单解析对象
    const form = new formidable.IncomingForm();
    // 设置客户端上传文件的存储路径
    form.uploadDir = path.join(__dirname, 'public', 'uploads');
    // 保留上传文件的后缀名字
    form.keepExtensions = true;
    // 解析客户端传递过来的FormData对象
    form.parse(req, (err, fields, files) => {
        // 将客户端传递过来的文件地址响应到客户端
        res.send({
            path: files.attrName.path.split('public')[1],
        });
    });
});

// 监听端口
app.listen(3000);
// 控制台提示输出
console.log('服务器启动成功');
```

![image-20220318164659326](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/ajax/image-20220318164659326.png)

## 二. Ajax 请求限制

注意：以下代码均在下面 s1 与 s2 文件结构中，public 下的文件为 html 页面，app.js 为服务器端代码

![image-20220318192952008](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/ajax/image-20220318192952008.png)

### 2.1 同源政策

如果两个页面拥有相同的协议、域名和端口，那么这两个页面就属于同一个源，其中只要有一个不相同，就是不同源。

-   `http://www.example.com/dir/page.html`
-   `http://www.example.com/dir2/other.html：同源`
-   `http://example.com/dir/other.html：不同源（域名不同）`
-   `http://v2.www.example.com/dir/other.html：不同源（域名不同）`
-   `http://www.example.com:81/dir/other.html：不同源（端口不同）`
-   `https://www.example.com/dir/page.html：不同源（协议不同）`

同源政策是为了保证用户信息的安全，防止恶意的网站窃取数据。最初的同源政策是指 A 网站在客户端设置的 Cookie，B 网站是不能访问的。随着互联网的发展，同源政策也越来越严格，在不同源的情况下，其中有一项规定就是无法向非同源地址发送 Ajax 请求，如果请求，浏览器就会报错。

现在有一个 A 网站、有一个 B 网站，A 网站中的 HTML 文件只能向 A 网站服务器中发送 Ajax 请求，B 网站中的 HTML 文件只能向 B 网站中发送 Ajax 请求，但是 A 网站是不能向 B 网站发送 Ajax 请求的，同理，B 网站也不能向 A 网站发送 Ajax 请求。那么如何解决这个问题呢？

### 2.2 JSONP（方法一）

jsonp 是 json with padding 的缩写，它不属于 Ajax 请求，但它可以模拟 Ajax 请求。

1. 将不同源的服务器端请求地址写在 script 标签的 src 属性中

```
<script src="www.example.com"></script>
```

2. 服务器端响应数据必须是一个函数的调用，真正要发送给客户端的数据需要作为函数调用的参数。

```
const data = 'fn({name: "张三", age: "20"})';
res.send(data);
```

3. 在客户端全局作用域下定义函数 fn

```
function fn (data) { }
```

4. 在 fn 函数内部对服务器端返回的数据进行处理

```
function fn (data) { console.log(data); }
```

这里使用 nodejs 创建两个服务器，分别为 s1 和 s2，把两个服务器都打开

s1 的 app.js

```javascript
// 引入express框架
const express = require('express');
// 路径处理模块
const path = require('path');
// 向其他服务器端请求数据的模块
const request = require('request');
// 创建web服务器
const app = express();
// 静态资源访问服务功能
app.use(express.static(path.join(__dirname, 'public')));

app.get('/server', (req, res) => {
    request('http://localhost:3001/cross', (err, response, body) => {
        res.send(body);
    });
});

// 监听端口
app.listen(3000);
// 控制台提示输出
console.log('服务器启动成功');
```

s2 的 app.js

```javascript
// 引入express框架
const express = require('express');
// 路径处理模块
const path = require('path');
// 接收post请求参数
const formidable = require('formidable');
// 实现session功能
var session = require('express-session');
// 创建web服务器
const app = express();
// 接收post请求参数
// 实现session功能
app.use(
    session({
        secret: 'keyboard cat',
        resave: false,
        saveUninitialized: false,
    })
);

// 静态资源访问服务功能
app.use(express.static(path.join(__dirname, 'public')));

app.get('/better', (req, res) => {
    // 接收客户端传递过来的函数的名称
    //const fnName = req.query.callback;
    // 将函数名称对应的函数调用代码返回给客户端
    //const data = JSON.stringify({name: "张三"});
    //const result = fnName + '('+ data +')';
    // setTimeout(() => {
    // 	res.send(result);
    // }, 1000)
    res.jsonp({ name: 'lisi', age: 20 });
});

// 监听端口
app.listen(3001);
// 控制台提示输出
console.log('服务器启动成功');
```

在 s1 的 public 文件夹下面创建`使用jsonp向非同源服务器端请求数据.html`，添加以下代码

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
    </head>
    <body>
        <button id="btn">点我发送请求</button>
        <script>
            function fn2(data) {
                console.log('客户端的fn函数被调用了');
                console.log(data);
            }
        </script>
        <script type="text/javascript">
            // 获取按钮
            var btn = document.getElementById('btn');
            // 为按钮添加点击事件
            btn.onclick = function () {
                // 创建script标签
                var script = document.createElement('script');
                // 设置src属性
                script.src = 'http://localhost:3001/better?callback=fn2';
                // 将script标签追加到页面中
                document.body.appendChild(script);
                // 为script标签添加onload事件
                script.onload = function () {
                    // 将body中的script标签删除掉
                    document.body.removeChild(script);
                };
            };
        </script>
    </body>
</html>
```

### 2.3 JSONP 封装

```javascript
function jsonp(options) {
    // 动态创建script标签
    var script = document.createElement('script');
    // 拼接字符串的变量
    var params = '';

    for (var attr in options.data) {
        params += '&' + attr + '=' + options.data[attr];
    }

    // myJsonp0124741
    var fnName = 'myJsonp' + Math.random().toString().replace('.', '');
    // 它已经不是一个全局函数了
    // 我们要想办法将它变成全局函数
    window[fnName] = options.success;
    // 为script标签添加src属性
    script.src = options.url + '?callback=' + fnName + params;
    // 将script标签追加到页面中
    document.body.appendChild(script);
    // 为script标签添加onload事件
    script.onload = function () {
        document.body.removeChild(script);
    };
}
```

### 2.4 **CORS** 跨域资源共享（方法二）

CORS：**全称为 Cross-origin resource sharing**，即跨域资源共享，它允许浏览器向跨域服务器发送 Ajax 请求，克服了 Ajax 只能同源使用的限制。

![image-20220318190245142](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/ajax/image-20220318190245142.png)

只需要在 s2 的 app.js 中设置 CORS 即可实现 s1 的服务器能发起请求，并得到响应

```
// 拦截所有请求
app.use((req, res, next) => {
	// 1.允许哪些客户端访问我
	// * 代表允许所有的客户端访问我
	// 注意：如果跨域请求中涉及到cookie信息传递，值不可以为*号 比如是具体的域名信息
	res.header('Access-Control-Allow-Origin', 'http://localhost:3000')
	// 2.允许客户端使用哪些请求方法访问我
	res.header('Access-Control-Allow-Methods', 'get,post')
	// 允许客户端发送跨域请求时携带cookie信息
	res.header('Access-Control-Allow-Credentials', true);
	next();
});
```

### 2.5 服务器端解决（方法三）

同源政策是浏览器给予 Ajax 技术的限制，服务器端是不存在同源政策限制。服务端可通过`request模块`访问其他服务端

![image-20220318190710526](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/ajax/image-20220318190710526.png)

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
    </head>
    <body>
        <button id="btn">点我发送请求</button>
        <script src="/js/ajax.js"></script>
        <script>
            // 获取按钮
            var btn = document.getElementById('btn');
            // 为按钮添加点击事件
            btn.onclick = function () {
                ajax({
                    type: 'get',
                    url: 'http://localhost:3000/server',
                    success: function (data) {
                        console.log(data);
                    },
                });
            };
        </script>
    </body>
</html>
```

服务端 s1 的 app.js

```javascript
// 引入express框架
const express = require('express');
// 路径处理模块
const path = require('path');
// 向其他服务器端请求数据的模块
const request = require('request');
// 创建web服务器
const app = express();
// 静态资源访问服务功能
app.use(express.static(path.join(__dirname, 'public')));

app.get('/server', (req, res) => {
    request('http://localhost:3001/cross', (err, response, body) => {
        res.send(body);
    });
});

// 监听端口
app.listen(3000);
// 控制台提示输出
console.log('服务器启动成功');
```

服务端 s2 的 app.js

```
// 引入express框架
const express = require('express');
// 路径处理模块
const path = require('path');
// 接收post请求参数
const formidable = require('formidable');
// 创建web服务器
const app = express();
// 接收post请求参数

// 静态资源访问服务功能
app.use(express.static(path.join(__dirname, 'public')));

app.get('/cross', (req, res) => {
	res.send('ok')
});

// 监听端口
app.listen(3001);
// 控制台提示输出
console.log('服务器启动成功');
```

### 2.6 实现跨域登录功能

在 s1 的 public 下新建`实现跨域登录功能.html`

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>实现跨域功能</title>
	<link rel="stylesheet" href="/assets/bootstrap/dist/css/bootstrap.min.css">
	<style type="text/css">
		.container {
			padding-top: 60px;
		}
	</style>
</head>
<body>
	<div class="container">
		<form id="loginForm">
			<div class="form-group">
				<label>用户名</label>
				<input type="text" name="username" class="form-control" placeholder="请输入用户名">
			</div>
			<div class="form-group">
				<label>密码</label>
				<input type="password" name="password" class="form-control" placeholder="请输入用密码">
			</div>
			<input type="button" class="btn btn-default" value="登录" id="loginBtn">
			<input type="button" class="btn btn-default" value="检测用户登录状态" id="checkLogin">
		</form>
	</div>
	<script type="text/javascript">
		// 获取登录按钮
		var loginBtn = document.getElementById('loginBtn');
		// 获取检测登录状态按钮
		var checkLogin = document.getElementById('checkLogin');
		// 获取登录表单
		var loginForm = document.getElementById('loginForm');
		// 为登录按钮添加点击事件
		loginBtn.onclick = function () {
			// 将html表单转换为formData表单对象
			var formData = new FormData(loginForm);
			// 创建ajax对象
			var xhr = new XMLHttpRequest();
			// 对ajax对象进行配置
			xhr.open('post', 'http://localhost:3001/login');
			// 当发送跨域请求时，携带cookie信息
			xhr.withCredentials = true;
			// 发送请求并传递请求参数
			xhr.send(formData);
			// 监听服务器端给予的响应内容
			xhr.onload = function () {
				console.log(xhr.responseText);
			}
		}

		// 当检测用户状态按钮被点击时
		checkLogin.onclick = function () {
			// 创建ajax对象
			var xhr = new XMLHttpRequest();
			// 对ajax对象进行配置
			xhr.open('get', 'http://localhost:3001/checkLogin');
			// 当发送跨域请求时，携带cookie信息
			xhr.withCredentials = true;
			// 发送请求并传递请求参数
			xhr.send();
			// 监听服务器端给予的响应内容
			xhr.onload = function () {
				console.log(xhr.responseText);
			}
		}
	</script>
</body>
</html>
```

s2 服务端的的 app.js

```javascript
// 引入express框架
const express = require('express');
// 路径处理模块
const path = require('path');
// 接收post请求参数
const formidable = require('formidable');
// 实现session功能
var session = require('express-session');
// 创建web服务器
const app = express();
// 接收post请求参数
// 实现session功能
app.use(
    session({
        secret: 'keyboard cat',
        resave: false,
        saveUninitialized: false,
    })
);

// 静态资源访问服务功能
app.use(express.static(path.join(__dirname, 'public')));

// 拦截所有请求
app.use((req, res, next) => {
    // 1.允许哪些客户端访问我
    // * 代表允许所有的客户端访问我
    // 注意：如果跨域请求中涉及到cookie信息传递，值不可以为*号 比如是具体的域名信息
    res.header('Access-Control-Allow-Origin', 'http://localhost:3000');
    // 2.允许客户端使用哪些请求方法访问我
    res.header('Access-Control-Allow-Methods', 'get,post');
    // 允许客户端发送跨域请求时携带cookie信息
    res.header('Access-Control-Allow-Credentials', true);
    next();
});

app.post('/login', (req, res) => {
    // 创建表单解析对象
    var form = formidable.IncomingForm();
    // 解析表单
    form.parse(req, (err, fields, file) => {
        // 接收客户端传递过来的用户名和密码
        const { username, password } = fields;
        // 用户名密码比对
        if (username == 'itheima' && password == '123456') {
            // 设置session
            req.session.isLogin = true;
            res.send({ message: '登录成功' });
        } else {
            res.send({ message: '登录失败, 用户名或密码错误' });
        }
    });
});

app.get('/checkLogin', (req, res) => {
    // 判断用户是否处于登录状态
    if (req.session.isLogin) {
        res.send({ message: '处于登录状态' });
    } else {
        res.send({ message: '处于未登录状态' });
    }
});

// 监听端口
app.listen(3001);
// 控制台提示输出
console.log('服务器启动成功');
```

## 三. JQuery 中的 Ajax

### 3.1 $.ajax()方法

JQuery 的$.ajax()方法完成了 ajax 的封装，

```javascript
$.ajax({
	//请求方式
     type: 'get',
     //请求地址
     url: 'http://www.example.com',
     // 向服务器端发送的请求参数,如果是json
     data: { name: 'zhangsan', age: '20' },
     contentType: 'application/json',
',	// 向服务器端发送的请求参数,如果是key=value&key=value
     //data: 'name=zhangsan&age=100',
     //contentType: 'application/x-www-form-urlencoded',
     beforeSend: function () {
         return false
     },
     // 请求成功以后函数被调用
     success: function (response) {
     // response为服务器端返回的数据
	// 方法内部会自动将json字符串转换为json对象
	 console.log(response);
     },
     // 请求失败以后函数被调用
     error: function (xhr) {}
});
```

> 注意：如果是 json 对象`var params = {name: 'wangwu', age: 300}`不能直接赋给 data，必须通过 JSON.stringify()方法转换为 json 字符串，如

```javascript
var params = { name: 'wangwu', age: 300 };
$.ajax({
    // 请求方式
    type: 'post',
    // 请求地址
    url: '/user',
    // 向服务器端发送的请求参数
    data: JSON.stringify(params),
    // 指定参数的格式类型
    contentType: 'application/json',
    // 请求成功以后函数被调用
    success: function (response) {
        // response为服务器端返回的数据
        // 方法内部会自动将json字符串转换为json对象
        console.log(response);
    },
});
```

如果想要在发起请求前做点事情，可通过`beforeSend`设置，下面设置阻止发起请求。

```javascript
// 在请求发送之前调用
beforeSend: function () {
alert('请求不会被发送')
// 请求不会被发送
return false;
},
```

### 3.2 serialize 方法

通过 serialize 方法可将表单中的数据自动拼接成字符串类型的参数进行传递

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>serialize方法说明</title>
</head>
<body>
	<form id="form">
		<input type="text" name="username">
		<input type="password" name="password">
		<input type="submit" value="提交">
	</form>
	<script src="/js/jquery.min.js"></script>
	<script type="text/javascript">
		$('#form').on('submit', function () {
			// 将表单内容拼接成字符串类型的参数
			var params = $('#form').serialize();
			console.log(params)
			return false;
		});
	</script>
</body>
</html>
```

但是这样显得不够灵活，不能对各个参数进行操作，为此我们可以自己封装一个函数，在返回一个 json 对象进行参数传递

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>serialize方法说明</title>
</head>
<body>
	<form id="form">
		<input type="text" name="username">
		<input type="password" name="password">
		<input type="submit" value="提交">
	</form>
	<script src="/js/jquery.min.js"></script>
	<script type="text/javascript">
		$('#form').on('submit', function () {
			let data=serializeObject($(this));
			console.log(data);
		});

		// 将表单中用户输入的内容转换为对象类型
		function serializeObject (obj) {
			// 处理结果对象
			var result = {};
			// [{name: 'username', value: '用户输入的内容'}, {name: 'password', value: '123456'}]
			var params = obj.serializeArray();
			// 循环数组 将数组转换为对象类型
			$.each(params, function (index, value) {
				result[value.name] = value.value;
			})
			// 将处理的结果返回到函数外部
			return result;
		}

	</script>
</body>
</html>
```

### 3.3 发送 jsonp 请求

使用$.ajax()可直接发送 json 请求，内部已经封装好了

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>$.ajax方法基本使用</title>
</head>
<body>
	<button id="btn">发送请求</button>
	<script src="/js/jquery.min.js"></script>
	<script>

		function fn (response) {
			console.log(response)
		}

		$('#btn').on('click', function () {
			$.ajax({
				url: '/jsonp',
				// 向服务器端传递函数名字的参数名称，不写默认是callback
				//jsonp: 'foo',
                // 向服务器端传递函数名字的参数名称,如果要使用其他函数可设置，不过不建议
				jsonpCallback: 'fn',
				// 代表现在要发送的是jsonp请求
				dataType: 'jsonp',

				success: function (response) {
					console.log(response)
				}
			})
		});
	</script>
</body>
</html>
```

### 3.4 \$.get(),\$.post()方法

相当于$.ajax()再进行简化了

```
$.get('http://www.example.com', {name: 'zhangsan', age: 30}, function (response) {})

$.post('http://www.example.com', {name: 'lisi', age: 22}, function (response) {})

```

### 3.5 RESTful 风格的 API

当向服务端发送请求，为了规范而避免引起错误，定义了 RESTful 风格的 API，而在$.ajax 中按这种风格进行了封装

```
GET：      获取数据
POST：    添加数据
PUT：      更新数据
DELETE： 删除数据
```

具体实现

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
    </head>
    <body>
        <script src="/js/jquery.min.js"></script>
        <script type="text/javascript">
            // 获取用户列表信息
            $.ajax({
                type: 'get',
                url: '/users',
                success: function (response) {
                    console.log(response);
                },
            });

            // 获取id为10的用户信息
            $.ajax({
                type: 'get',
                url: '/users/10',
                success: function (response) {
                    console.log(response);
                },
            });

            // 获取id为10的用户信息
            $.ajax({
                type: 'delete',
                url: '/users/10',
                success: function (response) {
                    console.log(response);
                },
            });

            // 获取id为10的用户信息
            $.ajax({
                type: 'put',
                url: '/users/10',
                success: function (response) {
                    console.log(response);
                },
            });
        </script>
    </body>
</html>
```

## 四. XML

XML 的全称是 extensible markup language，代表可扩展标记语言，它的作用是传输和存储数据。在

```xml
<students>
     <student>
         <sid>001</sid>
         <name>张三</name>
         </student>
     <student>
         <sid>002</sid>
         <name>王二丫</name>
         </student>
 </students>
```

在 ajax 中可通过`XMLHttpRequest`对象的`responseXML`属性得到服务端发送过来的 xml 数据

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
    </head>
    <body>
        <button id="btn">发送请求</button>
        <div id="container"></div>
        <script type="text/javascript">
            var btn = document.getElementById('btn');
            var container = document.getElementById('container');

            btn.onclick = function () {
                var xhr = new XMLHttpRequest();
                xhr.open('get', '/xml');
                xhr.send();
                xhr.onload = function () {
                    // xhr.responseXML 获取服务器端返回的xml数据
                    var xmlDocument = xhr.responseXML;
                    var title =
                        xmlDocument.getElementsByTagName('title')[0].innerHTML;
                    container.innerHTML = title;
                };
            };
        </script>
    </body>
</html>
```

服务端

```javascript
app.get('/xml', (req, res) => {
    res.header('content-type', 'text/xml');
    res.send(
        '<message><title>消息标题</title><content>消息内容</content></message>'
    );
});
```
