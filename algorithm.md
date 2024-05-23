### 获取列表中的唯一元素：可以看出来set在对数字列表操作时，返回的结果有排列效果
```python
A = ["a","d","c","a"]
B = list(set(A))
print(B) # B = ['d', 'a', 'c']

A = [2,1,3,-2,-1,2,]
B = list(set(A))
print(B) # B = [1, 2, 3, -1, -2]
```

### 获取列表中每个元素的数量：
- method1：Counter函数
```python
from collections import Counter

my_list = ["a","d","c","a",1,1,2]

element_counts = Counter(my_list)
print(element_counts) # Counter({'a': 2, 1: 2, 'd': 1, 'c': 1, 2: 1})
```
- method2: 字典循环
```python
my_list = ["a","d","c","a",1,1,2]

element_counts = {}
for element in my_list:
    if element in element_counts:
        element_counts[element] += 1
    else:
        element_counts[element] = 1

print(element_counts) # {'a': 2, 'd': 1, 'c': 1, 1: 2, 2: 1}
```

20240523