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

## Scrapy���
���棺ͨ�Ž�ͨվ
�����������У�Requests�����Ŷ�
�������������������أ����غú�Response�ش������������
����Spiders��Xpath������Ƚ������ԣ���������Response��Ӧ����ȡ����
�ܵ�����װȥ���ࡢ�洢�ࡢ������ϴ
�����м��download middlewares���Զ�����չ����װ����
�����м�����Զ�����չ���޸�Requests/Response

https://movie.douban.com/top250

## ����
�½���Ŀ
scrapy startproject douban
scrapy genspider douban_spider movie.douban.com	#�����ļ�
��ȷĿ�꣺���ƣ���ţ����������ݣ���Ϣ����item�ĵ�
�������棬��Spyder�ĵ�
�洢����

scrapy crawl douban_spider













