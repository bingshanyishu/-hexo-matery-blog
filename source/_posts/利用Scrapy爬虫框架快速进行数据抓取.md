---
title: 利用Scrapy爬虫框架快速进行数据抓取
author: Sankey
coverImg: /medias/banner/1.jpg
top: false
cover: false
toc: true
mathjax: false
tags:
  - 爬虫 
  - scrapy
categories:
  - 技能之树
reprintPolicy: cc_by
abbrlink: 202203081831
date: 2022-03-08 18:31:33
summary:
img:
password:
---

## 利用Scrapy爬虫框架快速进行数据抓取

> 你逆光而来，配得上世间所有的美好。

## 一. 基础概述

Scrapy的基础概述与安装，有大佬已经写的很详细了，具体可去看看大佬的文章，下面是文章链接

[Scrapy爬虫框架，入门案例（非常详细）_ck784101777的博客-CSDN博客_scrapy](https://blog.csdn.net/ck784101777/article/details/104468780)

我这里就加一些文章里没有的东西吧**→\_→      ←\_←**



## 二. 存储到MySQL

在管道pipelines.py文件中添加一个新的类

```python
#添加一个Mysql管道
class MysqlPipeline(object):
	#数据库初始化
    def open_spider(self,spider):
    	#连接到mysql数据库
        self.db=pymysql.connect(
            host=MYSQL_HOST,
            user=MYSQL_USER,
            password=MYSQL_PWD,
            database=MYSQL_DB,
            charset=MYSQL_CHAR
        )
        #创建游标操作数据库
        self.cursor=self.db.cursor()

	#数据库的操作
    def process_item(self, item, spider):
        ins='insert into films value(%s,%s,%s)'
        #插入时间，演员，上映时间
        L=[item['name'],item['star'],item['time']]
        self.cursor.execute(ins,L)
        #提交数据库
        self.db.commit()
        return item

	#关闭数据库
    def close_spidr(self,spider):
        #关闭游标
        self.cursor.close()
        #关闭数据库
        self.db.close()
```

在settings.py中定义数据库信息，默认已经建好了数据库

```python
#添加数据库配置信息
MYSQL_HOST='localhost'
MYSQL_USER='root'
MYSQL_PWD='123456'
MYSQL_DB='filmsdb'
MYSQL_CHAR='utf8'

将ITEM_PIPELINES取消注释，并添加Mysql管道配置
ITEM_PIPELINES = {
   'Maoyan_thread.pipelines.MaoyanThreadPipeline': 300,# 400表示权重
   #添加Mysql管道配置
   'Maoyan_thread.pipelines.MysqlPipeline': 500,# 权重值越小，越优先执行！
}
```

**PIPELINES管道配置的一些注意事项**

1. 使用之前需要在settings中开启
2. pipeline在setting中键表示位置(即pipeline在项目中的位置可以自定义)，值表示距离引擎的远近，越近数据会越先经过：权重值小的优先执行
3. 有多个pipeline的时候，process_item的方法必须return item,否则后一个pipeline取到的数据为None值
4. pipeline中process_item的方法必须有，否则item没有办法接受和处理
5. process_item方法接受item和spider，其中spider表示当前传递item过来的spider
6. open_spider(spider) :能够在爬虫开启的时候执行一次
7. close_spider(spider) :能够在爬虫关闭的时候执行一次
8. 上述俩个方法经常用于爬虫和数据库的交互，在爬虫开启的时候建立和数据库的连接，在爬虫关闭
    的时候断开和数据库的连接



## 三. 非结构化的数据存储

使用scrapy框架我们除了要下载文本，还有可能需要下载图片，scrapy提供了ImagePipeline来进行图片的下载。

这里以爬取360图片/美女为例来进行说明，话不多说，直接开始

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-GqqespVL-1646291370487)(https://gitee.com/Omnivore_zhang/cloud-image/raw/master/Spider/image-20220302195243757.png)]



先创建个scrapy项目，我命名为**So**，这里创建项目默认已经会了，不会的去看**基础概述一**

然后找到spiders文件夹下的so.py，再SoSpider类中添加下面代码

```python
name = 'so'
    allowed_domains = ['image.so.com']
    #注释start_urls
    # start_urls = ['http://image.so.com/']
    url='https://image.so.com/zjl?ch=beauty&sn={}'
    #多线程，重写start_requests方法
    def start_requests(self):
        #爬取4页的数据
        for sn in range(0,100,30):
            url=self.url.format(sn)
            yield scrapy.Request(
                url=url,
                callback=self.parse_page
            )

    def parse_page(self, response):
        # 将json转换为字典
        html=json.loads(response.text)
        print(html)
        #创建item对象
        item=SoItem()
        for img in html['list']:
            item['img_link']=img['qhimg_url']
            item['img_title']=img['title']
            yield item  #甩给了管道文件

```



在管道中添加一个类，添加以下方法

```python
#导入ImagesPipeline
from scrapy.pipelines.images import ImagesPipeline
#继承管道类ImagesPipeline类
class SoPipeline(ImagesPipeline):
    def get_media_requests(self, item, info):
        print(item)
        yield scrapy.Request(
            url=item['img_link'],
            meta= {'title':item['img_title']}
        )
    def file_path(self, request, response=None, info=None, *, item=None):
        title=request.meta['title']
        filename = title + "." + request.url.split('.')[-1]
        return filename
```

items.py文件中添加数据定义

```python
class SoItem(scrapy.Item):
    # define the fields for your item here like:
    # name = scrapy.Field()
    img_link=scrapy.Field()
    img_title=scrapy.Field()
```

settings.py中配置

```python
#配置日志权限
LOG_LEVEL='WARNING'

#配置相片路径
IMAGES_STORE='images/'

#关闭机器人协议
ROBOTSTXT_OBEY = False
```

大概就可以了，重点就是继承`ImagesPipeline`类



## 四. scrapy shell的使用

使用scrapy shell可以测试网址的url,headers,还能通过先通过xpath获取网页元素再写到代码中，减少调试次数

基本使用

```python
http://httpbin.org/get
# scrapy shell URL地址 直接在cmd中写
scrapy shell http://www.baidu.com
*1、request.url : 请求URL地址
*2、request.headers ：请求头(字典)
*3、reqeust.meta ：item数据传递，定义代理(字典)
4、response.text ：字符串
5、response.body ：bytes
6、response.xpath('/html/head/title/text()').get()#更真实
exit();#退出
```



## 五. 设置随机User-Agent

通过改变User-Agent，可降低被爬取网址检测到的风险。

### 5.1 少量的User-Agent

**方法一**：

在settings.py中设置

```python
#取消注释，添加User-Agent
USER_AGENT = 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.102 Safari/537.36 Edg/98.0.1108.62'

或者设置在
DEFAULT_REQUEST_HEADERS = {
  'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8',
  'Accept-Language': 'en',
  'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.102 Safari/537.36 Edg/98.0.1108.62'
  
}
```

**方法二**:

在spider文件中的yield里面进行设置

```python
# spider
yield scrapy.Request(url,callback=函数名,headers={
'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.102 Safari/537.36 Edg/98.0.1108.62'
})
```



### 5.2 大量的User-Agent

middlewares.py设置中间件

```python
1、获取User-Agent
# 方法1 ：新建useragents.py,存放大量User-Agent，random模块随机切换
# 方法2 ：安装fake_useragent模块(sudo pip3 install fack_useragent)
from fake_useragent import UserAgent
ua_obj = UserAgent()
ua = ua_obj.random

2、middlewares.py新建中间件类
class RandomUseragentMiddleware(object):
    def process_request(self,reuqest,spider):
        ua = UserAgent()
        request.headers['User-Agent'] = ua.random

3、settings.py添加此下载器中间件

DOWNLOADER_MIDDLEWARES = {
   # 'Douban.middlewares.DoubanDownloaderMiddleware': 543,
    'Douban.middlewares.RandomUseragentMiddleware':300
}

```



## 六. 设置随机代理

```python
1、新建一个proxies.py，定义一个列表，用于存储所有的代理IP
proxies_list=[xxxx,xxxx,xxxx,xxxx,xxxx]

2、middlewares.py新建中间件类
class RandomProxyDownloaderMiddleware(object):
    def process_request(self,request,spider):
    	request.meta['proxy'] = proxies_list.chioce()
    def process_exception(self,request,exception,spider):
    	return request

3、settings.py添加此下载器中间件

DOWNLOADER_MIDDLEWARES = {
   # 'Douban.middlewares.DoubanDownloaderMiddleware': 543,
    'Douban.middlewares.RandomProxyDownloaderMiddleware':300
}
```





## 七. 设置cookies

有的网址需要设置cookies才能进行访问

**方法一**

直接在settings中设置

```
#取消这里的注释，让后添加cookies
DEFAULT_REQUEST_HEADERS = {
  'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8',
  'Accept-Language': 'en',
  'Cookie': 'OUTFOX_SEARCH_USER_ID=-2094518326@10.110.96.159; OUTFOX_SEARCH_USER_ID_NCOO=654528686.5393351; JSESSIONID=aaabc05LV06Lq7Stpyd9x; ___rl__test__cookies=1646102934467',
}

然后再取消Disable cookies的注释，注意其值必须是False才行
# Disable cookies (enabled by default)
COOKIES_ENABLED = False
```



**方法二**

在spiders下面中的解析文件设置

```python
#添加方法，返回为字典类型
def get_cookie(self):
	cs='OUTFOX_SEARCH_USER_ID=-2094518326@10.110.96.159; OUTFOX_SEARCH_USER_ID_NCOO=654528686.5393351; JSESSIONID=aaabc05LV06Lq7Stpyd9x; ___rl__test__cookies=1646102934467'
    cs_list=cs.split(';')
    cs_dict={}
    for c in cs_list:
    	cs_dict[c.split('=')[0]]=c.split('=')[1]
    return cs_dict
```

然后yield里面直接赋值

```
yield scrapy.FormRequest(
            url=post_url,
            formdata=data,
            callback=self.parse,
            cookies=self.get_cookie()

        )
```





**方法三**

在middlewares.py中添加类

```python
class YoudaoCOookie(object):
    def get_cookie(self):
        cs = 'OUTFOX_SEARCH_USER_ID=-2094518326@10.110.96.159; OUTFOX_SEARCH_USER_ID_NCOO=654528686.5393351; JSESSIONID=aaabc05LV06Lq7Stpyd9x; ___rl__test__cookies=1646102934467'
        cs_list = cs.split(';')
        cs_dict = {}
        for c in cs_list:
            cs_dict[c.split('=')[0]] = c.split('=')[1]
        return cs_dict

    def process_request(self,request,spider):
        request.cookies=self.get_cookie()
```

然后在settings中设置

```python
DOWNLOADER_MIDDLEWARES = {
   # 'Youdao.middlewares.YoudaoDownloaderMiddleware': 543,
  'Youdao.middlewares.YoudaoCOookie':500
}

```
