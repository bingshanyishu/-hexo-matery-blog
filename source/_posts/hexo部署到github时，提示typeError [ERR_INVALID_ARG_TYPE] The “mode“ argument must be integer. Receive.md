---
title: hexo部署到github时，提示typeError
author: Sankey
coverImg: /medias/banner/1.jpg
top: false
cover: false
toc: true
mathjax: false
tags:
  - Blog问题
categories:
  - 项目之树
abbrlink: 4b2340a4
reprintPolicy: cc_by
date: 2022-01-31 00:00:00
img:
password:
summary: 'hexo部署到github时，提示typeError [ERR_INVALID_ARG_TYPE]: The “mode“ argument must be integer. Receive... '


---



# hexo部署到github时，提示typeError [ERR_INVALID_ARG_TYPE]: The “mode“ argument must be integer. Receive...

## 一. 错误情况

在部署部署博客时，遇到这个错误，

```
$ hexo d
INFO  Deploying: git
INFO  Clearing .deploy_git folder...
INFO  Copying files from public folder...
FATAL Something's wrong. Maybe you can find the solution here: https://hexo.io/docs/troubleshooting.html
TypeError [ERR_INVALID_ARG_TYPE]: The "mode" argument must be integer. Received an instance of Object
    at copyFile (fs.js:2040:10)
    at tryCatcher (D:\HexoBlog\node_modules\bluebird\js\release\util.js:16:23)
    at ret (eval at makeNodePromisifiedEval (C:\Users\27532\AppData\Roaming\npm\node_modules\hexo-cli\node_modules\bluebird\js\release\promisify.js:184:12), <anonymous>:13:39)
    at D:\HexoBlog\node_modules\hexo-fs\lib\fs.js:144:39
    at tryCatcher (D:\HexoBlog\node_modules\bluebird\js\release\util.js:16:23)
    at Promise._settlePromiseFromHandler (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:517:31)
    at Promise._settlePromise (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:574:18)
    at Promise._settlePromise0 (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:619:10)
    at Promise._settlePromises (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:699:18)
    at Promise._fulfill (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:643:18)
    at Promise._resolveCallback (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:437:57)
    at Promise._settlePromiseFromHandler (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:529:17)
    at Promise._settlePromise (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:574:18)
    at Promise._settlePromise0 (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:619:10)
    at Promise._settlePromises (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:699:18)
    at Promise._fulfill (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:643:18)
    at Promise._resolveCallback (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:437:57)
    at Promise._settlePromiseFromHandler (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:529:17)
    at Promise._settlePromise (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:574:18)
    at Promise._settlePromise0 (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:619:10)
    at Promise._settlePromises (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:699:18)
    at Promise._fulfill (D:\HexoBlog\node_modules\bluebird\js\release\promise.js:643:18)
```



## 二. 解决方法

查阅相关文章得知，是[node](https://so.csdn.net/so/search?q=node&spm=1001.2101.3001.7020)版本过高导致的

查看了我的版本号

```
$ hexo -v
hexo: 3.9.0
hexo-cli: 4.3.0
os: win32 10.0.19042
node: 14.17.5
v8: 8.4.371.23-node.76
uv: 1.41.0
zlib: 1.2.11
brotli: 1.0.9
ares: 1.17.2
modules: 83
nghttp2: 1.42.0
napi: 8
llhttp: 2.1.3
openssl: 1.1.1k
cldr: 39.0
icu: 69.1
tz: 2021a
unicode: 13.0
```

hexo 版本才3.9.0,

而node 版本已经是14.17.5了

更换版本

[Releases · coreybutler/nvm-windows (github.com)](https://github.com/coreybutler/nvm-windows/releases)下载nvm

安装

![image-20220118152346612](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Blog/question/image-20220118152346612.png)

[(5条消息) Node版本的升级和降级之node版本管理工具nvm_Pioneer-CSDN博客_nvm升级node版本](https://blog.csdn.net/chengliang666/article/details/119571718)

[windows如何把已安装的nodejs高版本降级为低版本(图文教程)_node.js_脚本之家 (jb51.net)](https://www.jb51.net/article/202124.htm)

## 三. 附常用nvm命令

查看安装过的node版本 `nvm list`

![image-20220118152440873](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Blog/question/image-20220118152440873.png)

安装某个版本`nvm install <version>`

![image-20220118152521897](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Blog/question/image-20220118152521897.png)

使用某个版本 `nvm use<version>`

载某个node版本 `nvm uninstall <version>`

如果出现乱码

![image-20220118152208341](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Blog/question/image-20220118152208341.png)

更改了cmd的权限成功解决问题，以管理员运行cmd窗口，再输入nvm use 12.14.0解决问题



再运行 hexo d 成功解决

![image-20220118152746877](https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Blog/question/image-20220118152746877.png)



