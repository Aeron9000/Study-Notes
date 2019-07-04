## Numpy



```python
import numpy as np
array=np.array([[1,2,3],
						[2,3,4]])
print(array)
print('几维num of dim:',array.ndim)
print('行*列shape:',array.shape)
print('总共元素size:',array.size)

array=np.array([2,23,44],dtype=np.int)
b=np.arange(4)				#[0,1,2,3]
array=np.zeros((2,5))
array=np.ones((2,5))
array=np.empty((2,5),dtype=float)
array=np.arange(14,2,-1)
array=np.arange(12).reshape((3,4))
array=np.linspace(1,10,8).reshape((2,4))		#生产线段数列，可以reshape
a=np.random.random((2,4))
print(np.argmin(a))		#最小值索引
print(np.max(a))
print(np.sum(a))
print(np.sum(a,axis=0)) #1对行计算，0对列计算
print(np.mean(a))
print(np.mean(a,axis=0))
print(a.mean())		#平均值
print(np.median(a))	#中位数

print(np.cumsum(a))	#逐步累加，输出个数=元素数，无关ndim
print(np.diff(a))		#累差，输出=列-1
print(np.nonzeron(a))	#输出非0的行数list，列数list
print(np.sort(a))		#逐行排列
print(np.transpose(a))
print((a.T).dot(a))
print(np.clip(a,5,9))	#所有大于9变成9

```

```python
c=np.sin(a)
print(a<3)					#列表，显示True或假。(a==3)	
c=a*b               #相同位置元素逐个相城
d=np.dot(a,b)       #点乘，各行*各列
d=a.dot*(b)
```

索引。
```python



```

```python



```

```python



```

## Pandas
























