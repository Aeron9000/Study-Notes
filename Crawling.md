
## 读取网址
```python
from urllib.request import urlopen
html=urlopen("http://pythonscraping.com/pages/page1.html")	#urlopen打开从网络获取的远程对象
print(html.read())
```

## Bs4
```python
from urllib.request import urlopen
from bs4 import BeautifulSoup									#bs4通过定位HTML标签，展现XML结构信息
html=urlopen("http://pythonscraping.com/pages/page1.html")
bsObj=BeautifulSoup(html.read(), "html.parser")				#用BeautifulSoup获取标签
print(bsObj.prettify())													#输出格式规整些
print(bsObj.h1)
```

## 常见异常处理
```python
#1.网页不存在时，urlopen抛出异常HTTPError；
#2.服务器不存在时，html返回None对象；
#3.调用不存在的标签的子标签时，发生AttributeError错误。
try:
	Content=bsObj.noneTag.subTag
except AttributeError as e:	
	print('Tag找不到')
else:
	if Content==None
		print('Tag找不到')
	else:
		print(Content)
```

完整版：
```python
from urllib.request import urlopen
from urllib.error import HTTPError
from bs4 import BeautifulSoup
def getTitle(url):
    try:
        html=urlopen(url)
    except HTTPError as e:										#网页不存在return None
        return None
    try:
        bsobj=BeautifulSoup(html.read(), "html.parser")
        title=bsobj.body.h1
    except AttributeError as e:									#不存在的标签的子标签
        return None
    return title												#如果body存在而h1不存在则title=None
title=getTitle("http://www.pythonscraping.com/pages/page1.html")
if title==None:
    print('Tag找不到')
else:
    print(title)
```

## 层叠样式表CSS
<span class="green">Anna Scherer</span>
寻找标签为span的属性class值=green的文本。

```python
from urllib.request import urlopen
from bs4 import BeautifulSoup
html=urlopen("http://pythonscraping.com/pages/warandpeace.html")
bsObj=BeautifulSoup(html, "html.parser")
nameList=bsObj.findAll("span",{"class":"green"})			#findAll(tag,Attri属性及值,,text内容,,)
for name in nameList:
    print(name.get_text())									#get_text()去除标签留下文字
Prince=bsObj.findAll(text="the prince")						#输出为纯文本无标签
print(len(Prince))											#标签次数
```

后代标签及兄弟标签
```python
from urllib.request import urlopen
from bs4 import BeautifulSoup
html=urlopen("http://pythonscraping.com/pages/page3.html")
bsObj=BeautifulSoup(html, "html.parser")
for child in bsObj.find("table",{"id":"giftList"}).children:				#后代标签
    print(child)
for sibling in bsObj.find("table",{"id":"giftList"}).tr.next_siblings:	#兄弟标签
    print(sibling)
```

## 加上正则表达式(Regular Expression)
```python
from urllib.request import urlopen
from bs4 import BeautifulSoup
import re         
html=urlopen("http://pythonscraping.com/pages/page3.html")
bsObj=BeautifulSoup(html, "html.parser")
images=bsObj.findAll("img",{"src":re.compile("\.\.\/img\/gifts/img.*\.jpg")})
# \转义 .任意单个字符 *表示0次或多次。所以规则是：../img/gifts/img1.jpg
for image in images:
    print(image["src"])
tag2=bsObj.findAll(lambda tag:len(tag.attrs)==2)				#获取具有两个属性的标签
```

## 维基百科六度分割理论
```python
import urllib.request
import urllib.parse
from bs4 import BeautifulSoup
html = urllib.request.urlopen("https://wikipedia.sogou.se/wiki/"+urllib.parse.quote("凯文·贝肯"))
bsObj = BeautifulSoup(html, "html.parser")
for link in bsObj.findAll("a"):						#标签a，属性href，值是要输出的链接
    if 'href' in link.attrs:
        print(link.attrs['href'])
```

```python
from urllib import request
import urllib.parse
from bs4 import BeautifulSoup
import re
url="https://wikipedia.sogou.se/wiki/"+urllib.parse.quote("凯文·贝肯")
html = request.urlopen(url)
bsObj = BeautifulSoup(html, "html.parser")
for link in bsObj.find("div",{"id":"bodyContent"}).findAll("a",{"href":re.compile("^(/wiki/)((?!:).)*$")}):		#注意'id'引号，写成href=re..时没有字典{}括号
    print(link.attrs['href'])
```

从一个链接中循环获得下一个链接。
```python
from urllib import request
import urllib.parse
from bs4 import BeautifulSoup
import re
import random
import datetime

def getLinks(url):
    html = request.urlopen("https://wikipedia.sogou.se"+url)
    bsObj = BeautifulSoup(html, "html.parser")
    return bsObj.find("div",{"id":"bodyContent"}).findAll("a",{"href":re.compile("^(/wiki/)((?!:).)*$")})	#findAll结果是列表ResultSet

random.seed(datetime.datetime.now())
url = "/wiki/" + urllib.parse.quote("凯文·贝肯")				#多个字符串编码用parse.urlencode()。encode编码成UTF-8码，decode解码回Unicode
linkList = getLinks(url)
while len(linkList)>0:
    nextLink=linkList[random.randint(0,len(linkList)-1)].attrs['href']	#href属性值只有后半段链接
    print(urllib.parse.unquote(nextLink))			#解码成中文unquote
    linkList=getLinks(nextLink)
```

```python



```

```python



```

```python



```