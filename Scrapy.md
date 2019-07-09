## 大纲
Scrapy简介
Scrapy安装
Mongodb安装
Scrapy框架、组件、数据流
Scrapy抓取

## Linux上安装Scrapy
```Linux
cd
ls
pwd
pip3 install scrapy
yum install -y openssl-devel
sudo
./configure --prefix='/home/user_what/python3' --with-ssl	#Python是编译安装，到个人目录下安装，不影响别人项目
make
make install

rz				#pypi 网站去下载Twisted模块，后导入文件
mv ...tar.bz2 soft/
tar -xvjf 	#解压缩
python3 setup.py install	#安装Twisted模块
cd python3/bin
```

多线程+头部信息、封装代理+封装数据去重类、存储类、异常检测机制
Scrapy：纯Python实现的框架，基于Twisted的异步处理框架

## Scrapy组件介绍
引擎：通信交通站
调度器：队列，Requests请求排队
下载器：发送请求并下载，下载好后Response回答给引擎后给爬虫
爬虫Spiders：Xpath或正则等解析策略，处理所有Response回应，提取数据
管道：封装去重类、存储类、数据清洗
下载中间件download middlewares：自定义扩展，封装代理
爬虫中间件：自定义扩展，修改Requests/Response

## 例子
步骤：
1.新建项目
	scrapy startproject douban
	scrapy genspider douban_spider movie.douban.com		#爬虫文件
2.明确目标：名称，序号，描述，导演，信息，在item文档
3.建立爬虫，在Spyder文档
4.存储数据

Settings.py文件中修改: USER_AGENT。

在items.py文档定义：
```python
class DoubanItem(scrapy.Item):
    # name = scrapy.Field()
    serial_number=scrapy.Field()
    movie_name=scrapy.Field()
```

命令行中输入"scrapy crawl douban_spider"，或者在建立的main.py文件里：
```python
from scrapy import cmdline
cmdline.execute('scrapy crawl douban_spider'.split())
```


1. 在douban_spider.py文件中修改，初次爬取：
```python
import scrapy
class DoubanSpiderSpider(scrapy.Spider):
    name = 'douban_spider'								#爬虫名
    allowed_domains = ['movie.douban.com']		#允许的域名
	start_urls = ['https://movie.douban.com/top250']		#入口url，扔到Schedule里
    #解析
	def parse(self, response):		
        print(response.text)
```

2. 爬取电影序号：
```python
import scrapy
from douban.items import DoubanItem
class DoubanSpiderSpider(scrapy.Spider):
	#省略......
    #解析，提取序号
    def parse(self, response):
        movie_list=response.xpath("//div[@class='article']//ol[@class='grid_view']/li")
        for i_item in movie_list:
            douban_item=DoubanItem()
            douban_item['serial_number']=i_item.xpath(".//div[@class='item']//em/text()").extract_first()
            print(douban_item)
```

3. 加上电影信息：
```python
    #解析
    def parse(self, response):
        movie_list=response.xpath("//div[@class='article']//ol[@class='grid_view']/li")
        for i_item in movie_list:
            douban_item=DoubanItem()
            douban_item['serial_number']=i_item.xpath(".//div[@class='item']//em/text()").extract_first()
            douban_item['movie_name']=i_item.xpath(".//div[@class='info']/div[@class='hd']/a/span[1]/text()").extract_first()
            content=i_item.xpath(".//div[@class='info']//div[@class='bd']/p[1]/text()").extract()
            for i_content in content:
                content_s="".join(i_content.split())        #去掉空格
                douban_item['introduce']=content_s
            douban_item['star'] = i_item.xpath(".//span[@class='rating_num']/text()").extract_first()
            douban_item['evaluate'] = i_item.xpath(".//div[@class='star']//span[4]/text()").extract_first()
            douban_item['describe'] = i_item.xpath(".//p[@class='quote']/span/text()").extract_first()
            yield douban_item   #yield到管道里
		   
		   
```
