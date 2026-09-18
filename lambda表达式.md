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

| 对比维度 | 内置函数（Built-in Function） | 面向对象方法（Method） |
|---------|---------------------------|---------------------|
| 调用方式 | `函数名(参数)` | `对象.方法名(参数)` |
| 依赖关系 | 独立存在，不依赖任何对象 | 必须依附于某个对象/类 |
| 第一个参数 | 所有参数都需显式传入 | 第一个参数 `self` 由 Python 自动传入 |
| 作用范围 | 全局可用，随时调用 | 只能通过特定类型的对象调用 |
| 本质 | 解释器预定义的独立工具 | 定义在类内部的函数 |
常见内置函数：
```
abs(-5)          # 绝对值 → 5
sum([1,2,3])     # 求和 → 6
max(3, 7, 2)     # 最大值 → 7
min(3, 7, 2)     # 最小值 → 2
round(3.14)      # 四舍五入 → 3
pow(2, 3)        # 2的3次方 → 8
int("123")       # 字符串转整数 → 123
float(5)         # 整数转浮点 → 5.0
str(123)         # 整数转字符串 → "123"
list((1,2))      # 元组转列表 → [1, 2]
dict()           # 创建空字典
len([1,2,3])     # 长度 → 3
sorted([3,1,2])  # 排序 → [1, 2, 3]
reversed([1,2,3])# 反转迭代器
enumerate(["a","b"])  # 带索引 → (0,"a"), (1,"b")
zip([1,2], ["a","b"]) # 打包 → (1,"a"), (2,"b")
map(lambda x: x*2, [1,2,3])     # 映射
filter(lambda x: x>1, [1,2,3])  # 过滤
type("hello")       # 返回类型 → <class 'str'>
isinstance(5, int)  # 类型判断 → True
callable(print)     # 是否可调用 → True
all([True, True])   # 是否全为真 → True
any([False, True])  # 是否有真 → True
print("hello")   # 打印
input()          # 读取输入
open("file.txt") # 打开文件
```
常见面向对象方法（必须通过对象调用)
列表（list）的方法
```
lst = [1, 2, 3]
lst.append(4)      # 追加元素 → [1,2,3,4]
lst.pop()          # 弹出末尾 → 4, lst变为[1,2,3]
lst.sort()         # 原地排序
lst.reverse()      # 原地反转
lst.insert(0, 0)   # 指定位置插入
lst.remove(2)      # 删除指定值
```
字符串（str）的方法
```
s = "hello world"
s.upper()          # 转大写 → "HELLO WORLD"
s.lower()          # 转小写
s.split(" ")       # 分割 → ["hello", "world"]
s.replace("l", "x")# 替换 → "hexxo worxd"
s.strip()          # 去空白
s.find("world")    # 查找位置 → 6
```
字典（dict）的方法
```
d = {"name": "Alice", "age": 20}
d.keys()           # 所有键
d.values()         # 所有值
d.items()          # 所有键值对
d.get("name")      # 安全取值 → "Alice"
d.pop("age")       # 删除并返回值
```
集合（set）的方法
```
s = {1, 2, 3}
s.add(4)           # 添加元素
s.remove(2)        # 删除元素
s.union({3,4,5})   # 并集
s.intersection({2,3})  # 交集
```
### 快速判断技巧
看到一个调用时，问自己两个问题：
有没有点号 .？
有 → 是方法（如 lst.append()）
没有 → 是函数（如 len(lst)）
数据写在前面还是括号里？
数据在前，用 . 调用 → 方法
数据在括号里作为参数 → 函数

写法：
```
内置函数(数据, key=lambda 参数: 表达式)
内置函数(数据, lambda参数: 表达式)
```
