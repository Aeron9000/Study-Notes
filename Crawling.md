﻿
## 读取网址
```Pyhton
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
```python
## 异常处理
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



```python

```