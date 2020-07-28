# Task04：列表、元组和字符串

[TOC]

## 一、列表

简单数据类型

- 整型`<class 'int'>`
- 浮点型`<class 'float'>`
- 布尔型`<class 'bool'>`

容器数据类型

- 列表`<class 'list'>`
- 元组`<class 'tuple'>`
- 字典`<class 'dict'>`
- 集合`<class 'set'>`
- 字符串`<class 'str'>`

#### 补充知识：存储类型

> 存储模型，对象可以保存多少个值。如果只能保存一个值，是**<u>原子类型</u>**。如果可以保存多个值，是**<u>容器类型</u>**。
>
> 数值是原子类型，元组，列表，字典是容器类型。
>
> 考虑字符串，按道理，字符串应该是容器类型，因为它包含多个字符。但是，Python中没有字符类型，也就是没有字符的概念，因此，把字符串归为原子类型。

参考链接：https://www.cnblogs.com/nzbbody/p/3551862.html



### 1.1.列表的定义

列表是有序集合，没有固定大小，**<u>能够保存任意数量任意类型的 Python 对象</u>**，语法为 `[元素1, 元素2, ..., 元素n]`。

- 关键点是「中括号 []」和「逗号 ,」
- 中括号 把所有元素绑在一起
- 逗号 将每个元素一一分开

### 1.2. 列表的创建

- 利用range()创建列表

```python
x = list(range(10))
print(x, type(x))
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] <class 'list'>

x = list(range(1, 11, 2))
print(x, type(x))
# [1, 3, 5, 7, 9] <class 'list'>

x = list(range(10, 1, -2))
print(x, type(x))
# [10, 8, 6, 4, 2] <class 'list'>
```

- 利用推导式创建列表

```python
x = [0] * 5
print(x, type(x))
# [0, 0, 0, 0, 0] <class 'list'>

x = [i for i in range(10)]
print(x, type(x))
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] <class 'list'>

x = [i for i in range(10, 1, -2)]
print(x, type(x))
# [10, 8, 6, 4, 2] <class 'list'>

x = [i ** 2 for i in range(1, 10)]
print(x, type(x))
# [1, 4, 9, 16, 25, 36, 49, 64, 81] <class 'list'>

x = [i for i in range(100) if (i % 2) != 0 and (i % 3) == 0]
print(x, type(x))

# [3, 9, 15, 21, 27, 33, 39, 45, 51, 57, 63, 69, 75, 81, 87, 93, 99] <class 'list'>
```

- 创建一个4*3的二维数组

```python
x = [[1, 2, 3], [4, 5, 6], [7, 8, 9], [0, 0, 0]]
print(x, type(x))
# [[1, 2, 3], [4, 5, 6], [7, 8, 9], [0, 0, 0]] <class 'list'>
#Aaron：这里的二维数组类型仍然是list！

for i in x:
    print(i, type(i))
# [1, 2, 3] <class 'list'>
# [4, 5, 6] <class 'list'>
# [7, 8, 9] <class 'list'>
# [0, 0, 0] <class 'list'>

x = [[0 for col in range(3)] for row in range(4)]
print(x, type(x))
# [[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]] <class 'list'>

x[0][0] = 1
print(x, type(x))
# [[1, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]] <class 'list'>

x = [[0] * 3 for row in range(4)]
print(x, type(x))
# [[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]] <class 'list'>

x[1][1] = 1
print(x, type(x))
# [[0, 0, 0], [0, 1, 0], [0, 0, 0], [0, 0, 0]] <class 'list'>
```

注意：

> 由于list的元素可以是任何对象，因此列表中所保存的是对象的指针。即使保存一个简单的`[1,2,3]`，也有3个指针和3个整数对象。
>
> `x = [a] * 4`操作中，<u>**只是创建4个指向list的引用，所以一旦`a`改变，`x`中4个`a`也会随之改变**</u>。

```python
x = [[0] * 3] * 4
print(x, type(x))
# [[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]] <class 'list'>

x[0][0] = 1
print(x, type(x))
# [[1, 0, 0], [1, 0, 0], [1, 0, 0], [1, 0, 0]] <class 'list'>

a = [0] * 3
x = [a] * 4
print(x, type(x))
# [[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]] <class 'list'>

x[0][0] = 1
print(x, type(x))
# [[1, 0, 0], [1, 0, 0], [1, 0, 0], [1, 0, 0]] <class 'list'>
```

- 创建一个混合列表

【例子】

```python
mix = [1, 'lsgo', 3.14, [1, 2, 3]]
print(mix, type(mix))  
# [1, 'lsgo', 3.14, [1, 2, 3]] <class 'list'>
```

- 创建一个空列表

【例子】

```python
empty = []
print(empty, type(empty))  # [] <class 'list'>
```

列表不像元组，**列表内容可更改 (mutable)，因此附加 (`append`, `extend`)、插入 (`insert`)、删除 (`remove`, `pop`) 这些操作都可以用在它身上**。

### 1.3.向列表中添加元素

`list.append(obj)` 在列表末尾添加新的对象，**只接受一个参数，参数可以是任何数据类型，被追加的元素在 list 中保持着原结构类型**。

【例子】

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.append('Thursday')
print(x)  
# ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Thursday']

print(len(x))  # 6
```

**<u>此元素如果是一个 list，那么这个 list 将作为一个整体进行追加</u>**，注意`append()`和`extend()`的区别。

【例子】

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.append(['Thursday', 'Sunday'])
print(x)  
# ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', ['Thursday', 'Sunday']]

print(len(x))  # 6
```

- `list.extend(seq)` 在列表末尾**<u>一次性追加另一个序列中的多个值（用新列表扩展原来的列表）</u>**

【例子】

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.extend(['Thursday', 'Sunday'])
print(x)  
# ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Thursday', 'Sunday']

print(len(x))  # 7
```

**<u>严格来说 `append` 是追加，把一个东西整体添加在列表后，而 `extend` 是扩展，把一个东西里的所有元素添加在列表后。</u>**

- `list.insert(index, obj)` 在编号 `index` 位置插入 `obj`。

【例子】

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.insert(2, 'Sunday')
print(x)
# ['Monday', 'Tuesday', 'Sunday', 'Wednesday', 'Thursday', 'Friday']

print(len(x))  # 6
```

### 1.4.删除列表中的元素

- `list.remove(obj)` 移除列表中某个值的**<u>第一个匹配项</u>**

【例子】

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.remove('Monday')
print(x)  # ['Tuesday', 'Wednesday', 'Thursday', 'Friday']
```

- `list.pop([index=-1])` **<u>移除列表中的一个元素（默认最后一个元素）</u>**，并且返回该元素的值

【例子】

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
y = x.pop()
print(y)  # Friday

y = x.pop(0)
print(y)  # Monday

y = x.pop(-2)
print(y)  # Wednesday
print(x)  # ['Tuesday', 'Thursday']
```

**`remove` 和 `pop` 都可以删除元素，前者是指定具体要删除的元素，后者是指定一个索引。**

- `del var1[, var2 ……]` 删除单个或多个对象。

【例子】

如果知道要删除的元素在列表中的位置，可使用`del`语句。

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
del x[0:2]
print(x)  # ['Wednesday', 'Thursday', 'Friday']
```

> **注意：**
>
> **如果你要从列表中删除一个元素，且不再以任何方式使用它，就使用`del`语句；如果你要在删除元素后还能继续使用它，就使用方法`pop()`。**

### 5.获取列表中的元素

- 通过元素的索引值，从列表获取单个元素，列表索引值是从0开始的。将索引指定为-1，返回最后一个列表元素，索引 -2 返回倒数第二个列表元素，以此类推。

【例子】

```python
x = ['Monday', 'Tuesday', 'Wednesday', ['Thursday', 'Friday']]
print(x[0], type(x[0]))  # Monday <class 'str'>
print(x[-1], type(x[-1]))  # ['Thursday', 'Friday'] <class 'list'>
print(x[-2], type(x[-2]))  # Wednesday <class 'str'>
```

切片的通用写法是 `start : stop : step`

- 情况 1 - "start :"
- 以 `step` 为 1 (默认) 从编号 `start` 往列表尾部切片。

【例子】

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
print(x[3:])  # ['Thursday', 'Friday']
print(x[-3:])  # ['Wednesday', 'Thursday', 'Friday']
```

- 情况 2 - ": stop"
- 以 `step` 为 1 (默认) 从列表头部往编号 `stop` 切片。

【例子】

```python
week = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
print(week[:3])  # ['Monday', 'Tuesday', 'Wednesday']
print(week[:-3])  # ['Monday', 'Tuesday']
```

- 情况 3 - "start : stop"
- 以 `step` 为 1 (默认) 从编号 `start` 往编号 `stop` 切片。

【例子】

```python
week = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
print(week[1:3])  # ['Tuesday', 'Wednesday']
print(week[-3:-1])  # ['Wednesday', 'Thursday']
```

- 情况 4 - "start : stop : step"
- 以具体的 `step` 从编号 `start` 往编号 `stop` 切片。**注意最后把 `step` 设为 -1，相当于将列表反向排列。**

【例子】

```python
week = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
print(week[1:4:2])  # ['Tuesday', 'Thursday']
print(week[:4:2])  # ['Monday', 'Wednesday']
print(week[1::2])  # ['Tuesday', 'Thursday']
print(week[::-1])  
# ['Friday', 'Thursday', 'Wednesday', 'Tuesday', 'Monday']
```

- 情况 5 - " : "
- 复制列表中的所有元素（浅拷贝）。

【例子】

```python
week = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
print(week[:])  
# ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
```

【例子】**<u>浅拷贝与深拷贝</u>**

```python
list1 = [123, 456, 789, 213]
list2 = list1
list3 = list1[:]

print(list2)  # [123, 456, 789, 213]
print(list3)  # [123, 456, 789, 213]
list1.sort()
print(list2)  # [123, 213, 456, 789] 
print(list3)  # [123, 456, 789, 213]

list1 = [[123, 456], [789, 213]]
list2 = list1
list3 = list1[:]
print(list2)  # [[123, 456], [789, 213]]
print(list3)  # [[123, 456], [789, 213]]
list1[0][0] = 111
print(list2)  # [[111, 456], [789, 213]]
print(list3)  # [[111, 456], [789, 213]]
#
```

#### 补充知识：赋值、浅拷贝与深拷贝

**（1）赋值：简单的对象引用**
在python中，变量赋值实际上是简单的对象引用。在创建一个对象后，再把它赋给另一个变量的时候，python并没有拷贝这个对象，而只是简单地拷贝了这个对象的引用。

个人总结：x赋值给y，然后x值变化的时候，y指向的值并没有变；但是赋值给y的x若是list，并进行了排序操作，那么**<u>y也会跟着进行排序</u>**

![python-copy-1](https://img-blog.csdn.net/20180317164223748?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1l2ZXR0cmU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)



**（2）浅拷贝**

在python中，对一个对象进行浅拷贝，产生的对象是新的，其类型和原对象一样；但其内容不是新的，只是原对象的内容的引用。

python中以下这这几种方式来实现浅拷贝：

> - 完全切片操作：B = A[:]
> - 利用工厂函数：B = list(A) 或 B = dict(A) 等
> - 使用copy模块的copy函数：B = copy.copy(A)

个人总结：x浅拷贝给y，然后x值变化的时候，y指向的值并没有变；若赋值给y的x是list，并进行了排序操作，**<u>那么y指向的值仍没有变，不会跟着进行排序</u>**

```python
>>> import copy
>>> A = [10,[20,30]]
>>> B = copy.copy(A)

# 改变前：
>>> A,B
([10, [20, 30]], [10, [20, 30]])
>>> id(A),id(B)
(99615944L, 99670792L)
>>> [id(x) for x in A],[id(x) for x in B]
([91055472L, 99617160L], [91055472L, 99617160L])

>>> A[0] = 100
>>> A[1][1] = 300

# 改变后：
>>> A,B
([100, [20, 300]], [10, [20, 300]])
>>> id(A),id(B)
(99615944L, 99670792L)
>>> [id(x) for x in A],[id(x) for x in B]
([91057296L, 99617160L], [91055472L, 99617160L])
```

![浅拷贝](/Users/taolong/Downloads/浅拷贝.png)



**（3）深拷贝**

对于浅拷贝中的例子，如果希望修改 `A[1]` 的内容时 `B[1]` 的内容不跟着一起改变，就需要用到深拷贝：`copy.deepcopy()`

```python
>>> import copy
>>> A = [10,[20,30]]
>>> B = copy.deepcopy(A)

# 改变前：
>>> A,B
([10, [20, 30]], [10, [20, 30]])
>>> id(A),id(B)
(88462536L, 88478856L)
>>> [id(x) for x in A],[id(x) for x in B]
([80176496L, 88463752L], [80176496L, 88514952L])

>>> A[0] = 100
>>> A[1][1] = 300

# 改变后：
>>> A,B
([100, [20, 300]], [10, [20, 30]])
>>> id(A),id(B)
(88462536L, 88478856L)
>>> [id(x) for x in A],[id(x) for x in B]
([80178320L, 88463752L], [80176496L, 88514952L])
```

![python-copy-4](https://img-blog.csdn.net/20180317164602983?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1l2ZXR0cmU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

> **注意：**
>
> - 非容器类型（比如数字、字符串和其他“原子”类型的对象，像xrange对象等）没有被拷贝一说，浅拷贝是用完全切片操作来完成的
> - 如果tuple变量只包含原子类型对象，对它的深拷贝将不会进行 (另外，tuple的元素是不能修改的)
> - 将上面深拷贝的例子中的<u>**list类型改为tuple类型，即便使用深拷贝，也只能得到一个浅拷贝**</u>

————————————————
原文链接：https://blog.csdn.net/Yvettre/article/details/79593510

### 1.6.列表的常用操作符

- 等号操作符：`==`
- 连接操作符 `+`
- 重复操作符 `*`
- 成员关系操作符 `in`、`not in`

**<u>「等号 ==」，只有成员、成员位置都相同时才返回True</u>**。

列表拼接有两种方式，用「加号 +」和「乘号 *」，前者首尾拼接，后者复制拼接。

【例子】

```python
list1 = [123, 456]
list2 = [456, 123]
list3 = [123, 456]

print(list1 == list2)  # False
print(list1 == list3)  # True

list4 = list1 + list2  # extend()
print(list4)  # [123, 456, 456, 123]

list5 = list3 * 3
print(list5)  # [123, 456, 123, 456, 123, 456]

list3 *= 3
print(list3)  # [123, 456, 123, 456, 123, 456]

print(123 in list3)  # True
print(456 not in list3)  # False
```

> 注意：
>
> 前面三种方法（`append`, `extend`, `insert`）可对列表增加元素，它们没有返回值，是**<u>直接修改了原数据对象</u>**。 而将两个list相加，**<u>需要创建新的 list 对象，从而需要消耗额外的内存</u>**，特别是当 list 较大时，尽量不要使用 “+” 来添加list。

### 1.7.列表的其他方法

- `list.count(obj)` 统计某个元素在列表中出现的次数

【例子】

```python
list1 = [123, 456] * 3
print(list1)  # [123, 456, 123, 456, 123, 456]
num = list1.count(123)
print(num)  # 3
```

- `list.index(x[, start[, end]])` **<u>从列表中找出某个值第一个匹配项的索引位置</u>**

【例子】

```python
list1 = [123, 456] * 5
print(list1.index(123))  # 0
print(list1.index(123, 1))  # 2
print(list1.index(123, 3, 7))  # 4
```

- `list.reverse()` **<u>反向列表中元素</u>**

【例子】

```python
x = [123, 456, 789]
x.reverse()
print(x)  # [789, 456, 123]
```

> 注意：
>
> 1. 列表的内置函数reverse()，没有返回值，就地反转
> 2. 切片法的反转，有返回值，是列表类型

```python
#(1)
x=[1,2,3,4]
x[::-1]
#[4,3,2,1]

#但是这时候列表x没变
x
#[1,2,3,4]


#(2)
x=[1,2,3,4]
x=x[::-1]
x
#[4,3,2,1]
```

参考链接：https://www.cnblogs.com/chitangyuanlai/p/10703108.html



- `list.sort(key=None, reverse=False)` 对原列表进行排序。

> - `key` -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，**<u>指定可迭代对象中的一个元素来进行排序</u>**。
> - `reverse` -- 排序规则，`reverse = True` 降序， `reverse = False` **<u>升序（默认）</u>**。
> - **<u>该方法没有返回值，但是会对列表的对象进行排序。</u>**

【例子】

```python
x = [123, 456, 789, 213]
x.sort()
print(x)
# [123, 213, 456, 789]

x.sort(reverse=True)
print(x)
# [789, 456, 213, 123]


# 获取列表的第二个元素
def takeSecond(elem):
    return elem[1]


x = [(2, 2), (3, 4), (4, 1), (1, 3)]
x.sort(key=takeSecond)
print(x)
# [(4, 1), (2, 2), (1, 3), (3, 4)]

x.sort(key=lambda a: a[0])
print(x)
# [(1, 3), (2, 2), (3, 4), (4, 1)]
```

**参考文献**：

- https://www.runoob.com/python3/python3-tutorial.html
- https://www.bilibili.com/video/av4050443
- https://mp.weixin.qq.com/s/DZ589xEbOQ2QLtiq8mP1qQ





## 二、元组

「元组」定义语法为：`(元素1, 元素2, ..., 元素n)`

> - 小括号把所有元素绑在一起
> - 逗号将每个元素一一分开

### 2.1.创建和访问一个元组

> - Python 的元组与列表类似，不同之处在于**<u>tuple被创建后就不能对其进行修改，类似字符串</u>**。
> - 元组使用小括号，列表使用方括号。
> - 元组与列表类似，也用整数来对它进行索引 (indexing) 和切片 (slicing)。

【例子】

```python
t1 = (1, 10.31, 'python')
t2 = 1, 10.31, 'python'
print(t1, type(t1))
# (1, 10.31, 'python') <class 'tuple'>

print(t2, type(t2))
# (1, 10.31, 'python') <class 'tuple'>

tuple1 = (1, 2, 3, 4, 5, 6, 7, 8)
print(tuple1[1])  # 2
print(tuple1[5:])  # (6, 7, 8)
print(tuple1[:5])  # (1, 2, 3, 4, 5)
tuple2 = tuple1[:]
print(tuple2)  # (1, 2, 3, 4, 5, 6, 7, 8)
```

- 创建元组可以用小括号 ()，**<u>也可以什么都不用</u>**，为了可读性，建议还是用 ()。
- **<u>*元组中只包含一个元素时，需要在元素后面添加逗号*</u>**，否则括号会被当作运算符使用。

【例子】

```python
x = (1)
print(type(x))  # <class 'int'>
x = 2, 3, 4, 5
print(type(x))  # <class 'tuple'>
x = []
print(type(x))  # <class 'list'>
x = ()
print(type(x))  # <class 'tuple'>
#注意哦
x = (1,)
print(type(x))  # <class 'tuple'>
```

【例子】

```python
print(8 * (8))  # 64
print(8 * (8,))  # (8, 8, 8, 8, 8, 8, 8, 8)
```

【例子】**<u>创建二维元组。</u>**

```python
x = (1, 10.31, 'python'), ('data', 11)
print(x)
# ((1, 10.31, 'python'), ('data', 11))

print(x[0])
# (1, 10.31, 'python')
print(x[0][0], x[0][1], x[0][2])
# 1 10.31 python

print(x[0][0:2])
# (1, 10.31)
```



### 2.2.更新和删除一个元组

【例子】

```python
week = ('Monday', 'Tuesday', 'Thursday', 'Friday')
week = week[:2] + ('Wednesday',) + week[2:]
print(week)  # ('Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday')
```

【例子】元组有不可更改 (immutable) 的性质，**<u>因此不能直接给元组的元素赋值，但是只要元组中的元素可更改 (mutable)，那么我们可以直接更改其元素，注意这跟赋值其元素不同</u>**。

```python
t1 = (1, 2, 3, [4, 5, 6])
print(t1)  # (1, 2, 3, [4, 5, 6])

t1[3][0] = 9
print(t1)  # (1, 2, 3, [9, 5, 6])
```



### 2.3.元组相关的操作符

- 等号操作符：`==`
- 连接操作符 `+`
- 重复操作符 `*`
- 成员关系操作符 `in`、`not in`

「等号 ==」，只有**成员、成员位置都相同时**才返回True。

元组拼接有两种方式，用「加号 +」和「乘号 *」，前者首尾拼接，后者复制拼接。

【例子】

```python
t1 = (123, 456)
t2 = (456, 123)
t3 = (123, 456)

print(t1 == t2)  # False
print(t1 == t3)  # True

t4 = t1 + t2
print(t4)  # (123, 456, 456, 123)

t5 = t3 * 3
print(t5)  # (123, 456, 123, 456, 123, 456)

t3 *= 3
print(t3)  # (123, 456, 123, 456, 123, 456)

print(123 in t3)  # True
print(456 not in t3)  # False
```



### 2.4.内置方法

元组大小和内容都不可更改，因此只有 `count` 和 `index` 两种方法。

【例子】

```python
t = (1, 10.31, 'python')
print(t.count('python'))  # 1
print(t.index(10.31))  # 1
```

- `count('python')` 是记录在元组 `t` 中该元素出现几次，显然是 1 次
- `index(10.31)` 是找到该元素在元组 `t` 的索引，显然是 1

### 2.5.解压元组

【例子】解压（unpack）一维元组（有几个元素左边括号定义几个变量）

```python
t = (1, 10.31, 'python')
(a, b, c) = t
print(a, b, c)
# 1 10.31 python
```

【例子】解压二维元组（按照元组里的元组结构来定义变量）

```python
t = (1, 10.31, ('OK', 'python'))
(a, b, (c, d)) = t
print(a, b, c, d)
# 1 10.31 OK python
```

【例子】如果你只想要元组其中几个元素，**<u>用通配符「*」，英文叫 wildcard，在计算机语言中代表一个或多个元素</u>**。下例就是把多个元素丢给了 `rest` 变量。

```python
t = 1, 2, 3, 4, 5
a, b, *rest, c = t
print(a, b, c)  # 1 2 5
print(rest)  # [3, 4]
```

【例子】如果你根本不在乎 rest 变量，那么就用通配符「*」加上下划线「_」。

```python
t = 1, 2, 3, 4, 5
a, b, *_ = t
print(a, b)  # 1 2
```



### 2.6.练习

1、写出下面代码的执行结果和最终结果的类型

```python
a=(1, 2)*2
b=(1, )*2
c=(1)*2
print(a,type(a))
print(b,type(b))
print(c,type(c))
#(1, 2, 1, 2) <class 'tuple'>
#(1, 1) <class 'tuple'>
#2 <class 'int'>
```

2、拆包过程是什么？

```python
a,b=1,2
```

上述过程属于拆包吗？

可迭代对象拆包时，怎么赋值给占位符？

> 我认为不属于，原因如下。
>
> 拆包定义: 对于函数中的多个返回数据, **<u>去掉元组, 列表或者字典直接获取里面数据</u>**的过程.
>
> 这里面1，2只是赋值给a和b而已，类型并不是元祖，如果是a,b=(1,2)或者说t=1,2;a,b=t这两种都属于拆包。
>
> ----
>
> 有的时候，拆包后的元素我们不一定全部需要，对于不需要的元素可以用任意符号占位：”_“，”*“
>
> 使用 * 拆包出来的变量永远都是列表类型， 使用的时候不用再去判断类型



**注意：**

> - 拆包时要注意，需要拆的数据的个数要与变量的个数相同，否则程序会异常
> - 除了对元组拆包之外，还可以对列表、字典等拆包
> - **对字典拆包后获取的是字典的key值**, 而不是value值

参考链接：

- https://www.cnblogs.com/shen-qiang/p/8983782.html

- https://blog.csdn.net/codersClip/article/details/83270309



## 三、字符串

### 3.1.字符串的定义

> - Python 中字符串被定义为引号之间的字符集合。
> - Python 支持使用成对的 单引号 或 双引号。

【例子】

```python
t1 = 'i love Python!'
print(t1, type(t1))
# i love Python! <class 'str'>

t2 = "I love Python!"
print(t2, type(t2))
# I love Python! <class 'str'>

print(5 + 8)  # 13
print('5' + '8')  # 58
```

- Python 的常用转义字符

| 转义字符 | 描述            |
| -------- | --------------- |
| `\\`     | 反斜杠符号      |
| `\'`     | 单引号          |
| `\"`     | 双引号          |
| `\n`     | 换行            |
| `\t`     | 横向制表符(TAB) |
| `\r`     | 回车            |

【例子】**如果字符串中需要出现单引号或双引号，可以使用转义符号`\`对字符串中的符号进行转义**。

```python
print('let\'s go')  # let's go
print("let's go")  # let's go
print('C:\\now')  # C:\now
print("C:\\Program Files\\Intel\\Wifi\\Help")
# C:\Program Files\Intel\Wifi\Help
```

【例子】**<u>原始字符串</u>**只需要在字符串前边加一个英文字母 r 即可。

```python
print(r'C:\Program Files\Intel\Wifi\Help')  
# C:\Program Files\Intel\Wifi\Help
```

【例子】**<u>三引号允许一个字符串跨多行，字符串中可以包含换行符、制表符以及其他特殊字符</u>**。

```python
para_str = """这是一个多行字符串的实例
多行字符串可以使用制表符
TAB ( \t )。
也可以使用换行符 [ \n ]。
"""
print(para_str)
# 这是一个多行字符串的实例
# 多行字符串可以使用制表符
# TAB (    )。
# 也可以使用换行符 [
#  ]。

para_str = '''这是一个多行字符串的实例
多行字符串可以使用制表符
TAB ( \t )。
也可以使用换行符 [ \n ]。
'''
print(para_str)
# 这是一个多行字符串的实例
# 多行字符串可以使用制表符
# TAB ( 	 )。
# 也可以使用换行符 [ 
#  ]。
```



### 3.2.字符串的切片与拼接

- 类似于元组具有不可修改性
- 从 0 开始 (和 Java 一样)
- 切片通常写成 `start:end` 这种形式，包括「`start` 索引」对应的元素，不包括「`end`索引」对应的元素。
- 索引值可正可负，正索引从 0 开始，从左往右；负索引从 -1 开始，从右往左。使用负数索引时，会从最后一个元素开始计数。最后一个元素的位置编号是 -1。

【例子】

```python
str1 = 'I Love LsgoGroup'
print(str1[:6])  # I Love
print(str1[5])  # e
print(str1[:6] + " 插入的字符串 " + str1[6:])  
# I Love 插入的字符串  LsgoGroup

s = 'Python'
print(s)  # Python
print(s[2:4])  # th
print(s[-5:-2])  # yth
print(s[2])  # t
print(s[-1])  # n
```



### 3.3.字符串的常用内置方法

- `capitalize()` 将字符串的第一个字符转换为大写。

【例子】

```python
str2 = 'xiaoxie'
print(str2.capitalize())  # Xiaoxie
```

- `lower()` 转换字符串中所有大写字符为小写。
- `upper()` 转换字符串中的小写字母为大写。
- `swapcase()` **<u>将字符串中大写转换为小写，小写转换为大写。</u>**

【例子】

```python
str2 = "DAXIExiaoxie"
print(str2.lower())  # daxiexiaoxie
print(str2.upper())  # DAXIEXIAOXIE
print(str2.swapcase())  # daxieXIAOXIE
```

- `count(str, beg= 0,end=len(string))` 返回`str`在 string 里面出现的次数，如果`beg`或者`end`指定则返回指定范围内`str`出现的次数。

【例子】

```python
str2 = "DAXIExiaoxie"
print(str2.count('xi'))  # 2
```

- `endswith(suffix, beg=0, end=len(string))` 检查字符串是否以指定子字符串 `suffix` 结束，如果是，返回 True，否则返回 False。如果 `beg` 和 `end` 指定值，则在指定范围内检查。
- `startswith(substr, beg=0,end=len(string))` 检查字符串是否以指定子字符串 `substr` 开头，如果是，返回 True，否则返回 False。如果 `beg` 和 `end` 指定值，则在指定范围内检查。

【例子】

```python
str2 = "DAXIExiaoxie"
print(str2.endswith('ie'))  # True
print(str2.endswith('xi'))  # False
print(str2.startswith('Da'))  # False
print(str2.startswith('DA'))  # True
```

- `find(str, beg=0, end=len(string))` 检测 `str` 是否包含在字符串中，如果指定范围 `beg` 和 `end`，则检查是否包含在指定范围内，**<u>如果包含，返回开始的索引值，否则返回 -1</u>**。
- `rfind(str, beg=0,end=len(string))` 类似于 `find()` 函数，不过是**<u>从右边开始查找</u>**。

【例子】

```python
str2 = "DAXIExiaoxie"
print(str2.find('xi'))  # 5
print(str2.find('ix'))  # -1
print(str2.rfind('xi'))  # 9
```

- `isnumeric()` 如果字符串中**<u>只包含数字字符，则返回 True</u>**，否则返回 False。

【例子】

```python
str3 = '12345'
print(str3.isnumeric())  # True
str3 += 'a'
print(str3.isnumeric())  # False
```

- `ljust(width[, fillchar])`返回一个原字符串**左对齐**，并使用`fillchar`（默认空格）填充至长度`width`的新字符串。
- `rjust(width[, fillchar])`返回一个原字符串**右对齐**，并使用`fillchar`（默认空格）填充至长度`width`的新字符串。

【例子】

```python
str4 = '1101'
print(str4.ljust(8, '0'))  # 11010000
print(str4.rjust(8, '0'))  # 00001101
```

- `lstrip([chars])` 截掉字符串左边的**<u>空格或指定字符</u>**。
- `rstrip([chars])` 删除字符串末尾的**<u>空格或指定字符</u>**。
- `strip([chars])` 在字符串上执行`lstrip()`和`rstrip()`。

【例子】

```python
str5 = ' I Love LsgoGroup '
print(str5.lstrip())  # 'I Love LsgoGroup '
print(str5.lstrip().strip('I'))  # ' Love LsgoGroup '
print(str5.rstrip())  # ' I Love LsgoGroup'
print(str5.strip())  # 'I Love LsgoGroup'
print(str5.strip().strip('p'))  # 'I Love LsgoGrou'
```

- `partition(sub)` 找到子字符串sub，把字符串分为一个三元组`(pre_sub,sub,fol_sub)`，如果字符串中不包含sub则返回`('原字符串','','')`。
- `rpartition(sub)`类似于`partition()`方法，不过是从右边开始查找。

【例子】

```python
str5 = ' I Love LsgoGroup '
print(str5.strip().partition('o'))  # ('I L', 'o', 've LsgoGroup')
print(str5.strip().partition('m'))  # ('I Love LsgoGroup', '', '')
print(str5.strip().rpartition('o'))  # ('I Love LsgoGr', 'o', 'up')
```

- `replace(old, new [, max])` 把 将字符串中的`old`替换成`new`，如果`max`指定，则**替换不超过**`max`次。

【例子】

```python
str5 = ' I Love LsgoGroup '
print(str5.strip().replace('I', 'We'))  # We Love LsgoGroup
```

- `split(str="", num)` 不带参数**<u>默认是以空格为分隔符切片字符串</u>**，如果`num`参数有设置，则仅分隔`num`**<u>个子字符串</u>**，返回切片后的子字符串拼接的列表。

【例子】

```python
str5 = ' I Love LsgoGroup '
print(str5.strip().split())  # ['I', 'Love', 'LsgoGroup']
print(str5.strip().split('o'))  # ['I L', 've Lsg', 'Gr', 'up']
```

【例子】

```python
u = "www.baidu.com.cn"
# 使用默认分隔符
print(u.split())  # ['www.baidu.com.cn']

# 以"."为分隔符
print((u.split('.')))  # ['www', 'baidu', 'com', 'cn']

# 分割0次
print((u.split(".", 0)))  # ['www.baidu.com.cn']

# 分割一次
print((u.split(".", 1)))  # ['www', 'baidu.com.cn']

# 分割两次
print(u.split(".", 2))  # ['www', 'baidu', 'com.cn']

# 分割两次，并取序列为1的项
print((u.split(".", 2)[1]))  # baidu

# 分割两次，并把分割后的三个部分保存到三个变量
u1, u2, u3 = u.split(".", 2)
print(u1)  # www
print(u2)  # baidu
print(u3)  # com.cn
```

【例子】去掉换行符

```python
c = '''say
hello
baby'''

print(c)
# say
# hello
# baby

print(c.split('\n'))  # ['say', 'hello', 'baby']
```

【例子】

```python
string = "hello boy<[www.baidu.com]>byebye"
print(string.split('[')[1].split(']')[0])  # www.baidu.com
print(string.split('[')[1].split(']')[0].split('.'))  # ['www', 'baidu', 'com']
```

- `splitlines([keepends])` 按照行('\r', '\r\n', \n')分隔，返回一个包含各行作为元素的列表，如果参数`keepends`为 False，不包含换行符，如果为 True，则保留换行符。

【例子】

```python
str6 = 'I \n Love \n LsgoGroup'
print(str6.splitlines())  # ['I ', ' Love ', ' LsgoGroup']
print(str6.splitlines(True))  # ['I \n', ' Love \n', ' LsgoGroup']
```

- `maketrans(intab, outtab)` 创建字符映射的转换表，第一个参数是字符串，表示需要转换的字符，第二个参数也是字符串表示转换的目标。
- `translate(table, deletechars="")` 根据参数`table`给出的表，转换字符串的字符，要过滤掉的字符放到`deletechars`参数中。

【例子】

```python
str7 = 'this is string example....wow!!!'
intab = 'aeiou'
outtab = '12345'
trantab = str7.maketrans(intab, outtab)
print(trantab)  # {97: 49, 111: 52, 117: 53, 101: 50, 105: 51}
print(str7.translate(trantab))  # th3s 3s str3ng 2x1mpl2....w4w!!!
```



### 3.4.字符串格式化

- `format` 格式化函数

【例子】

```python
str8 = "{0} Love {1}".format('I', 'Lsgogroup')  # 位置参数
print(str8)  # I Love Lsgogroup

str8 = "{a} Love {b}".format(a='I', b='Lsgogroup')  # 关键字参数
print(str8)  # I Love Lsgogroup

str8 = "{0} Love {b}".format('I', b='Lsgogroup')  # 位置参数要在关键字参数之前
print(str8)  # I Love Lsgogroup

str8 = '{0:.2f}{1}'.format(27.658, 'GB')  # 保留小数点后两位
print(str8)  # 27.66GB
```

- Python 字符串格式化符号

| 符 号 | 描述                                 |
| ----- | ------------------------------------ |
| %c    | 格式化字符及其ASCII码                |
| %s    | 格式化字符串，用str()方法处理对象    |
| %r    | 格式化字符串，用rper()方法处理对象   |
| %d    | 格式化整数                           |
| %o    | 格式化无符号八进制数                 |
| %x    | 格式化无符号十六进制数               |
| %X    | 格式化无符号十六进制数（大写）       |
| %f    | 格式化浮点数字，可指定小数点后的精度 |
| %e    | 用科学计数法格式化浮点数             |
| %E    | 作用同%e，用科学计数法格式化浮点数   |
| %g    | 根据值的大小决定使用%f或%e           |
| %G    | 作用同%g，根据值的大小决定使用%f或%E |

【例子】

```python
print('%c' % 97)  # a
print('%c %c %c' % (97, 98, 99))  # a b c
print('%d + %d = %d' % (4, 5, 9))  # 4 + 5 = 9
print("我叫 %s 今年 %d 岁!" % ('小明', 10))  # 我叫 小明 今年 10 岁!
print('%o' % 10)  # 12
print('%x' % 10)  # a
print('%X' % 10)  # A
print('%f' % 27.658)  # 27.658000
print('%e' % 27.658)  # 2.765800e+01
print('%E' % 27.658)  # 2.765800E+01
print('%g' % 27.658)  # 27.658
text = "I am %d years old." % 22
print("I said: %s." % text)  # I said: I am 22 years old..
print("I said: %r." % text)  # I said: 'I am 22 years old.'
```

- 格式化操作符辅助指令

| 符号  | 功能                                                         |
| ----- | ------------------------------------------------------------ |
| `m.n` | m 是显示的最小总宽度,n 是小数点后的位数（如果可用的话）      |
| `-`   | 用作左对齐                                                   |
| `+`   | 在正数前面显示加号( + )                                      |
| `#`   | 在八进制数前面显示零('0')，在十六进制前面显示'0x'或者'0X'(取决于用的是'x'还是'X') |
| `0`   | 显示的数字前面填充'0'而不是默认的空格                        |

【例子】

```python
print('%5.1f' % 27.658)  # ' 27.7'
print('%.2e' % 27.658)  # 2.77e+01
print('%10d' % 10)  # '        10'
print('%-10d' % 10)  # '10        '
print('%+d' % 10)  # +10
print('%#o' % 10)  # 0o12
print('%#x' % 108)  # 0x6c
print('%010d' % 5)  # 0000000005
```