���ֲ��ң�O(log n)������ʱ��
�򵥲��ң�O(n)������ʱ��
���������⣺O(n!)���׳�ʱ��

���飺�ڴ����������У�����ֱ�ӿ�������������ʣ���������Ҫ�����ź���λ��ʱҪ����ȥ��ĵط���
�����ڴ���������ã�������Ҫ���ϵ��°�·���ң�˳����ʣ�����������š�

ѡ���������ζ�ȡ��ѡminȻ������O(n^2*n^2)��1/2ʡ�ԡ�
```python
def findSmallest(arr):
    small_index=0
    small_value=arr[0]
    for i in range(1,len(arr)):
        if small_value > arr[i]:
            small_value = arr[i]
            small_index=i
    return small_index
def Sequence(arr):
    newArr=[]
    for j in range(len(arr)):
        min=findSmallest(arr)
        newarr.append(arr.pop(min))		#pop����������
    return newArr
arr1=[2,7,1,4,3]
print(Sequence(arr1))
```

ջStack��һ�����ݽṹ������push����pop������ȳ�LIFO

�ݹ飺
















