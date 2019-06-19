
## 读取网址
```python
from urllib.request import urlopen
html=urlopen("http://pythonscraping.com/pages/page1.html")
print(html.read())
```

## Bs4
```python
from urllib.request import urlopen
from bs4 import BeautifulSoup
html=urlopen("http://pythonscraping.com/pages/page1.html")
bsObj=BeautifulSoup(html.read(), "html.parser")
print(bsObj.h1)
```

## 异常处理
```python
#网页不存在urlopen抛出异常HTTPError；
#服务器不存在html返回None对象；
#调用不存在的标签的子标签时，发生AttributeError错误。

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
    except HTTPError as e:
        return None
    try:
        bsobj=BeautifulSoup(html.read(), "html.parser")
        title=bsobj.body.h1
    except AttributeError as e:
        return None
    return title
title=getTitle("http://www.pythonscraping.com/pages/page1.html")
if title==None:
    print('Tag找不到')
else:
    print(title)
```

## 层叠样式表CSS
```python
from urllib.request import urlopen
from bs4 import BeautifulSoup
html=urlopen("http://pythonscraping.com/pages/warandpeace.html")
bsObj=BeautifulSoup(html, "html.parser")
nameList=bsObj.findAll("span",{"class":"green"})
for name in nameList:
    print(name.get_text())
```

## 加上正则表达式Regular Expression
```python
from urllib.request import urlopen
from bs4 import BeautifulSoup
import re
html=urlopen("http://pythonscraping.com/pages/page3.html")
bsObj=BeautifulSoup(html, "html.parser")
images=bsObj.findAll("img",{"src":re.compile("\.\.\/img\/gifts/img.*\.jpg")})
for image in images:
    print(image["src"])
```

```python


```






