【cmd中环境配置】
```
conda create --name py3 python=3.7      #创建一个新的python环境，python版本为3.7，环境名称为py3
conda env list /conda info -e           #显示已创建的环境，会列出所有的环境名和对应路径
activate py3                            #切换到环境名为py3的环境，切换后可通过python -V查看是否切换成功
deactivate py3                          #返回前一个python环境
conda create --name py31 --clone py3    #克隆环境，克隆一个名为py3的环境，新环境名为py31，两个环境配置相同
conda remove --name py3 --all           #删除py3环境
```

```
#!/usr/bin/env python			#为了按UTF-8编码读取，通常在文件开头写上这两行。
# -*- coding: utf-8 -*-
```

## 函数：
```
name=input('your name:')    		#返回字符串
a=int(a)    	 			#转为整数
b=str(a)    	 			#转为字符
65=ord('A')    	 			#字母换成ASCII
A=chr(65)      	 			#ASCII换字母
u'中文'.encode('utf-8')                 #Unicode字符u'xxx'转换为UTF-8编码
'\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8')	#UTF-8编码转换为Unicode字符
cmp(x, y)        			#比较函数。如果x<y，返回-1，如果x==y，返回0，如果x>y，返回1。
bool(1)          			#true
len(u'ABC')      			#返回字符串的长度
isinstance(x, (int, float))    		#数据类型检查。
str.replace('a', 'A')    		#替换
```

全部大写的变量名表示常量（人为规则）
```python
#ASCII：	A=65  
	a=95
	0=48
u'...'    				#Unicode字符串
'...'     				#UTF-8的字符串
'I\'m \"OK\"!'    			#如\t回退光标，\r回车，\t表示制表符，\\表示的字符就是\。用r''表示''内不转义
					#用'''...'''表示多行内容
```

## 数

0B二进制，0O八进制，0X十六进制。浮点数存在不确定尾数，10^-16处有
==等于
科学计数法4.3e-3

```python
x//y 整数除		  x%y余数		  x**y 幂运算
二元操作符			x+=y x=x+y
范围：整数>浮点数>复数

pow(2,15)		pow(x,y,[z])对z求模
abs(x)			商余divmod(x,y)			round(x,d) ：d小数位截取数。max(a,b,c,d...)
int()求整		float(x)变浮点			complex()变复数。
eval()去两边的引号
```

字符串
-----
'''多行字符。程序中字符串无公式可以当做注释。'''
切片[m,n,步长k]
逆序输出[::-1]

```python
x+y		字符串相加
n*s		复制n次	
x in s		判断是否在s里。

len()。str(x)。
hex()。oct()
chr(s)变unicode		       		#ord(s)将Uni变回字符。
print(s,end="") 			#输出不换行。
s.lower()				#全变小写。s.upper()全大写
s.split(",")				#被逗号分隔出列表类型，默认为空字符
s.count(sub)				#出现的次数
s.replace(old,new)			#替换
s.center(width[,fillchar]) 		#根据宽度居中，填充居中
s.strip(c) 				#去掉左右两侧c
s.join(er) 				#每个字符元素后加一个er
```

格式化：
```python
"{}啊啊啊{}不{}不不".format("时间","是",10)
"{0:=^20}".format("PYTHON")
: 填充 对齐<>^ 宽度 , 精度(浮点或字符长) 类型bcdox,ef%
```

在字符串内部，%s表示用字符串替换，%d表示用整数替换，有几个%?占位符，后面就跟几个变量或者值，顺序要对应好。
格式化整数和浮点数还可以指定是否补0和整数与小数的位数。字符串里%是普通字符就需要转义，用%%来表示一个%。
常见的占位符：%d整数，%f浮点数，%s字符串，%x十六进制整数。
```
'Hi, %s, you have $%d.' % ('Michael', 1000000)

'%2d-%02d' % (3, 1)
' 3-01'

'%.2f' % 3.1415926    	 		#保留两位小数
'3.14'

u'Hi, %s' % u'Michael'   		#Unicode替换保持一致
u'Hi, Michael'
```

# 序列
【set集合】：不可有可变对象
```
s = set([1, 2, 3])       		#是(list)
s.add(4)
s.remove(4)   		 		#删除元素
s1&s2   		 		#交集
s1|s2   		 		#并集
```

【tuple元组】：不可变
```python
classmates=('Michael','Bob','Tracy')    #()。不可变tuple中元素
t = (1,)    				#只有一个元素，有逗号为元组
t = ('a', 'b', ['A', 'B'])     		#tuple不可变，但其中列表可变。
t[2][0] = 'X'
```

【list列表】：可变
```python
classmates=['aa','bb','cc']     	#是[]
len(classmates)      			#获得元素个数
classmates[0]        			#第一个索引[0]
len(classmates)-1    			#最后一个元素的索引，或者直接写-1做索引。所以-2为倒数第2个。。。
classmates.append('Adam')    		#往list末尾追加 一个元素
classmates.insert(3, 'Jack')    	#把元素插入到指定的位置，注意第一个索引为0。替换是直接赋值。
classmates.pop()     			#删除末尾一个元素
classmates.pop(2)    			#删除某一个位置的元素，注意第一个索引是0。
s[2][1]    				#二维数组s中的小集合的[1]元素。
for i in l[:]:     			#遍历list时想修改这个list可以复制一个list。
l.sort()     				#list进行排序，可变性
l.sort(key=lambda x:x[1],reverse=True)
```

【dict字典】：无序。不能放入可变对象。键-值存储结构，最常用的key（不可变就行）是字符串。
```python
d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}    #是{键:值}
d['Adam'] = 67				#方括号里是键，若没有则会添加
'k' in d    				#通过in判断键是否存在。键是字符串。
d.keys()				#所有键，可以遍历但不是列表
d.values()
d.items()
d.get('k',<default>)			#k对应的值，否则返回default。很重要
d.pop('Bob')     			#用pop(键)方法，删除一个key及对应的value
d.popitem()				#随机取出一对，形成元祖
d.clear()				#删除所有对
len(d)
for k in d:				#遍历所有键
```

time库：
```python
time()计算机内部时间值。ctime()可读时间的字符串。gmmtime()。
strftime(tpl,t) 将gmtime时间格式化。控制符年份%Y，月%m，月名%B，%d日期，%A星期，%H小时，%p上下午
striptime(str,tpl)
计时。起始相减time.perf_conter()
休眠时间sleep(30)
```

函数：参数输入，函数体处理，结果return输出：IPO

## 组合数据类型

集合定义：元素唯一、无序、不可变{,,,}。{}是生成字典用的。
```python
S={"py",123,("Py",123)}
S2=Set("pypy123")
```
操作符：并差交补

## 分词
jieba库：分词三方库。
精确模式、全模式、搜索引擎模式。

```python
pip install jieba		#分词库
jieba.lcut(s)			#精确模式
jieba.lcut(s,cut_all=True)
jieba.cut_for_search(s)
jieba.add_word()
```

## 文件及数据格式化

文本文件就是长字符串。统一编码。
没有统一编码的是二进制文件。

文件句柄=open("文件名：绝对或相对路径",  模式：只读r，覆盖写w，创建写x，追加写a)  #t文本方式,b二进制。
#可用+。a+追加写并读文件。默认rt。如果不写入w+会清空文档。文档存在x会报错。

```python
读：
f.read(size)			#读入全部，适合小文件
f.readline(size)
f.readlines(hint)		#读入前hint行
写：
f.write(str)
f.writelines(list)		#元素为string的列表拼接写入
f.seek(offset)			#改变文件操作指针。0开头、2结尾。
关闭：句柄f.close()
```
