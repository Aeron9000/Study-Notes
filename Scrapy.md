## ���
Scrapy���
Scrapy��װ
Mongodb��װ
Scrapy��ܡ������������
Scrapyץȡ

## Linux�ϰ�װScrapy
```Linux
cd
ls
pwd
pip3 install scrapy
yum install -y openssl-devel
sudo
./configure --prefix='/home/user_what/python3' --with-ssl	#Python�Ǳ��밲װ��������Ŀ¼�°�װ����Ӱ�������Ŀ
make
make install

rz				#pypi ��վȥ����Twistedģ�飬�����ļ�
mv ...tar.bz2 soft/
tar -xvjf 	#��ѹ��
python3 setup.py install	#��װTwistedģ��
cd python3/bin
```

���߳�+ͷ����Ϣ����װ����+��װ����ȥ���ࡢ�洢�ࡢ�쳣������
Scrapy����Pythonʵ�ֵĿ�ܣ�����Twisted���첽������

## Scrapy�������
���棺ͨ�Ž�ͨվ
�����������У�Requests�����Ŷ�
�������������������أ����غú�Response�ش������������
����Spiders��Xpath������Ƚ������ԣ���������Response��Ӧ����ȡ����
�ܵ�����װȥ���ࡢ�洢�ࡢ������ϴ
�����м��download middlewares���Զ�����չ����װ����
�����м�����Զ�����չ���޸�Requests/Response

## ����
���裺
1.�½���Ŀ
	scrapy startproject douban
	scrapy genspider douban_spider movie.douban.com		#�����ļ�
2.��ȷĿ�꣺���ƣ���ţ����������ݣ���Ϣ����item�ĵ�
3.�������棬��Spyder�ĵ�
4.�洢����

Settings.py�ļ����޸�: USER_AGENT��

��items.py�ĵ����壺
```python
class DoubanItem(scrapy.Item):
    # name = scrapy.Field()
    serial_number=scrapy.Field()
    movie_name=scrapy.Field()
```

������������"scrapy crawl douban_spider"�������ڽ�����main.py�ļ��
```python
from scrapy import cmdline
cmdline.execute('scrapy crawl douban_spider'.split())
```


1. ��douban_spider.py�ļ����޸ģ�������ȡ��
```python
import scrapy
class DoubanSpiderSpider(scrapy.Spider):
    name = 'douban_spider'								#������
    allowed_domains = ['movie.douban.com']		#���������
	start_urls = ['https://movie.douban.com/top250']		#���url���ӵ�Schedule��
    #����
	def parse(self, response):		
        print(response.text)
```

2. ��ȡ��Ӱ��ţ�
```python
import scrapy
from douban.items import DoubanItem
class DoubanSpiderSpider(scrapy.Spider):
	#ʡ��......
    #��������ȡ���
    def parse(self, response):
        movie_list=response.xpath("//div[@class='article']//ol[@class='grid_view']/li")
        for i_item in movie_list:
            douban_item=DoubanItem()
            douban_item['serial_number']=i_item.xpath(".//div[@class='item']//em/text()").extract_first()
            print(douban_item)
```

3. ���ϵ�Ӱ��Ϣ��
```python
    #����
    def parse(self, response):
        movie_list=response.xpath("//div[@class='article']//ol[@class='grid_view']/li")
        for i_item in movie_list:
            douban_item=DoubanItem()
            douban_item['serial_number']=i_item.xpath(".//div[@class='item']//em/text()").extract_first()
            douban_item['movie_name']=i_item.xpath(".//div[@class='info']/div[@class='hd']/a/span[1]/text()").extract_first()
            content=i_item.xpath(".//div[@class='info']//div[@class='bd']/p[1]/text()").extract()
            for i_content in content:
                content_s="".join(i_content.split())        #ȥ���ո�
                douban_item['introduce']=content_s
            douban_item['star'] = i_item.xpath(".//span[@class='rating_num']/text()").extract_first()
            douban_item['evaluate'] = i_item.xpath(".//div[@class='star']//span[4]/text()").extract_first()
            douban_item['describe'] = i_item.xpath(".//p[@class='quote']/span/text()").extract_first()
            yield douban_item   #yield���ܵ���
		   
		   
```





