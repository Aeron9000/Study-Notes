## Numpy



```python
import numpy as np
array=np.array([[1,2,3],
						[2,3,4]])
print(array)
print('��άnum of dim:',array.ndim)
print('��*��shape:',array.shape)
print('�ܹ�Ԫ��size:',array.size)

array=np.array([2,23,44],dtype=np.int)
b=np.arange(4)				#[0,1,2,3]
array=np.zeros((2,5))
array=np.ones((2,5))
array=np.empty((2,5),dtype=float)
array=np.arange(14,2,-1)
array=np.arange(12).reshape((3,4))
array=np.linspace(1,10,8).reshape((2,4))		#�����߶����У�����reshape
a=np.random.random((2,4))
print(np.argmin(a))		#��Сֵ����
print(np.max(a))
print(np.sum(a))
print(np.sum(a,axis=0)) #1���м��㣬0���м���
print(np.mean(a))
print(np.mean(a,axis=0))
print(a.mean())		#ƽ��ֵ
print(np.median(a))	#��λ��

print(np.cumsum(a))	#���ۼӣ��������=Ԫ�������޹�ndim
print(np.diff(a))		#�۲���=��-1
print(np.nonzeron(a))	#�����0������list������list
print(np.sort(a))		#��������
print(np.transpose(a))
print((a.T).dot(a))
print(np.clip(a,5,9))	#���д���9���9

```

```python
c=np.sin(a)
print(a<3)					#�б���ʾTrue��١�(a==3)	
c=a*b               #��ͬλ��Ԫ��������
d=np.dot(a,b)       #��ˣ�����*����
d=a.dot*(b)
```

������
```python



```

```python



```

```python



```

## Pandas
























