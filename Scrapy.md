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

引擎：通信交通站
调度器：队列，Requests请求排队
下载：发送请求并下载，下载好后Response回答给引擎后给爬虫
爬虫Spiders：Xpath或正则等解析策略，处理所有Response回应，提取数据
管道：封装去重类、存储类、数据清洗

下载中间件download middlewares：自定义扩展，封装代理
爬虫中间件：自定义扩展，修改Requests/Response

http://movie.douban.com/

新建项目
scrapy startproject douban
scrapy genspider douban_spider movie.douban.com	#爬虫文件
明确目标
建立爬虫
存储数据
















