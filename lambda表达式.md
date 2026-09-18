## 常规：
```
def 函数名(参数1，参数2，...）：
   函数体第一行代码
   函数体第二行代码
    ...
    return 语句
```
## lambda:
```
lambda 参数1，参数2...，参数n：函数体代码
```
# 使用情景：
1.通常只有一行代码
2.函数作为参数的时候

eg:
常规：
```
def last_char(item):
    return item[-1]
names=["李磊","李明","贝克汉姆"]
name.sort(key=last_char)
print(names)
```
lambda:
```
names=["李磊","李明","贝克汉姆"]
name.sort(key=lambda item:item[-1])
print(names)
```

# 常见的使用：
### 排序：sorted() 和 list.sort()
按字典的某个值排序
```
students = [{"name": "Tom", "age": 20}, {"name": "Jerry", "age": 18}]
students.sort(key=lambda x: x["age"])
```
按元组的第二个元素排序
```
data = [("Alice", 25), ("Bob", 20)]
sorted_data = sorted(data, key=lambda x: x[1])
```
多级排序：先按年龄升序，年龄相同按成绩降序
```
students = [("Tom", 18, 90), ("Jerry", 18, 85)]
students.sort(key=lambda x: (x[1], -x[2]))
```
### 数据映射：map()
```
# 计算每个元素的平方
numbers = [1, 2, 3, 4]
squares = list(map(lambda x: x ** 2, numbers))
```
### 条件过滤：filter()
```
# 提取偶数
numbers = [1, 2, 3, 4, 5, 6]
evens = list(filter(lambda x: x % 2 == 0, numbers))  
```
### 累积计算：reduce()
```
# 求所有元素的乘积
from functools import reduce
numbers = [1, 2, 3, 4]
product = reduce(lambda x, y: x * y, numbers) 
```
### 求最大/最小值：max() 和 min()
```
students = [{"name": "Alice", "score": 90}, {"name": "Bob", "score": 85}]
best = max(students, key=lambda x: x["score"])
```


reverse=False（默认值）：升序，从小到大排列。
reverse=True：降序，从大到小排列。
**在原有内容基础上改动不用额外命名列表，如果要是需要额外找要先用整新的列表**
