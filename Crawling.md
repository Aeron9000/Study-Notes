
## 读取网址
```Pyhton
from urllib.request import urlopen
html=urlopen("http://pythonscraping.com/pages/page1.html")
print(html.read())
```

## Bs4
```Pyhton
from urllib.request import urlopen
from bs4 import BeautifilSoup
html=urlopen("http://pythonscraping.com/pages/page1.html")
bsObj=BeautifilSoup(html.read())
print(bsObj.h1)
```

## 异常处理
```Pyhton
try:
	html=urlopen("http://pythonscraping.com/pages/page1.html")
except HTTPError as e:
	print(e)
```



```Pyhton

```