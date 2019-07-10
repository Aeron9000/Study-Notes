二分查找：O(log n)，对数时间
简单查找：O(n)，线性时间
旅行商问题：O(n!)，阶乘时间

数组：内存中连续排列，查找直接看索引（随机访问），插入需要依次排后，无位置时要复制去别的地方。
链表：内存中随机放置，查找需要从上到下按路径找（顺序访问），插入随机放。

选择排序：依次读取比选min然后排序，O(n^2*n^2)，1/2省略。
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
        newarr.append(arr.pop(min))		#pop参数是索引
    return newArr
arr1=[2,7,1,4,3]
print(Sequence(arr1))
```

栈Stack：一种数据结构，推入push弹出pop，后进先出LIFO

递归：
















