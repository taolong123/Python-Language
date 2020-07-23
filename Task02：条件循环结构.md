# Task02：条件循环结构

[TOC]

### 一.条件语句

##### assert 关键词

- `assert`这个关键词我们称之为“断言”，当这个关键词后边的条件为 False 时，程序自动崩溃并抛出`AssertionError`的异常。

【例子】

```python
my_list = ['lsgogroup']
my_list.pop(0)
assert len(my_list) > 0

# AssertionError
```

- 在进行单元测试时，可以用来在**<u>程序中置入检查点，只有条件为 True 才能让程序正常工作</u>**。

【例子】

```python
assert 3 > 7

# AssertionError
```

### 二、循环语句

##### 2.1 while-else循环

```python
while 布尔表达式:
    代码块
else:
    代码块
```

**<u>当`while`循环正常执行完的情况下，执行`else`输出，如果`while`循环中执行了跳出循环的语句，比如 `break`，将不执行`else`代码块的内容。</u>**

【例子】

```python
count = 0
while count < 5:
    print("%d is  less than 5" % count)
    count = count + 1
else:
    print("%d is not less than 5" % count)
    
# 0 is  less than 5
# 1 is  less than 5
# 2 is  less than 5
# 3 is  less than 5
# 4 is  less than 5
# 5 is not less than 5
```

【例子】

```python
count = 0
while count < 5:
    print("%d is  less than 5" % count)
    count = 6
    break
else:
    print("%d is not less than 5" % count)

# 0 is  less than 5
```

##### 2.2 for循环

`for`循环是迭代循环，**在Python中相当于一个通用的序列迭代器，可以遍历任何有序序列**，如`str、list、tuple`等，也可以**遍历任何可迭代对象**，如`dict`。

```python
for 迭代变量 in 可迭代对象:
    代码块
```

每次循环，迭代变量被设置为可迭代对象的当前元素，提供给代码块使用。

【例子】

```python
member = ['张三', '李四', '刘德华', '刘六', '周润发']
for each in member:
    print(each)

# 张三
# 李四
# 刘德华
# 刘六
# 周润发

for i in range(len(member)):
    print(member[i])

# 张三
# 李四
# 刘德华
# 刘六
# 周润发
```

【例子】

```python
dic = {'a': 1, 'b': 2, 'c': 3, 'd': 4}

for key, value in dic.items():
    print(key, value, sep=':', end=' ')
    
# a:1 b:2 c:3 d:4 
```

【例子】

```python
dic = {'a': 1, 'b': 2, 'c': 3, 'd': 4}

for key in dic.keys():
    print(key, end=' ')
    
# a b c d 
```

【例子】

```python 
dic = {'a': 1, 'b': 2, 'c': 3, 'd': 4}

for value in dic.values():
    print(value, end=' ')
    
# 1 2 3 4
```

##### 2.3 for-else 循环

```python
for 迭代变量 in 可迭代对象:
    代码块
else:
    代码块
```

当`for`循环正常执行完的情况下，执行`else`输出，如果`for`循环中执行了跳出循环的语句，比如 `break`，将不执行`else`代码块的内容，**与`while - else`语句一样**。

【例子】

```python
for num in range(10, 20):  # 迭代 10 到 20 之间的数字
    for i in range(2, num):  # 根据因子迭代
        if num % i == 0:  # 确定第一个因子
            j = num / i  # 计算第二个因子
            print('%d 等于 %d * %d' % (num, i, j))
            break  # 跳出当前循环
    else:  # 循环的 else 部分
        print(num, '是一个质数')

# 10 等于 2 * 5
# 11 是一个质数
# 12 等于 2 * 6
# 13 是一个质数
# 14 等于 2 * 7
# 15 等于 3 * 5
# 16 等于 2 * 8
# 17 是一个质数
# 18 等于 2 * 9
# 19 是一个质数
```

##### 2.4 range()函数

```python
range([start,] stop[, step=1])
```

> - 这个BIF（Built-in functions）有三个参数，其中用中括号括起来的两个表示这两个参数是可选的。
> - `step=1` 表示第三个参数的默认值是1。
> - `range` 这个BIF的作用是生成一个从`start`参数的值开始到`stop`参数的值结束的**数字序列**，**<u>该序列包含`start`的值但不包含`stop`的值</u>**。

【例子】

```python
for i in range(2, 9):  # 不包含9
    print(i)

# 2
# 3
# 4
# 5
# 6
# 7
# 8
```

【例子】

```python
for i in range(1, 10, 2):
    print(i)

# 1
# 3
# 5
# 7
# 9
```

##### 2.5 enumerate()函数

```python
enumerate(sequence, [start=0])
```

> - sequence -- 一个序列、迭代器或其他支持迭代对象。
> - start -- 下标起始位置。
> - **返回 enumerate(枚举) 对象**

【例子】

```python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']
lst = list(enumerate(seasons))
print(lst)
# [(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
lst = list(enumerate(seasons, start=1))  # 下标从 1 开始
print(lst)
# [(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```

**`enumerate()`与 for 循环的结合使用**

```python 
for i, a in enumerate(A)
    do something with a  
```

用 `enumerate(A)` 不仅返回了 `A` 中的元素，还顺便给该元素一个索引值 (默认从 0 开始)。此外，用 `enumerate(A, j)` 还可以确定索引起始值为 `j`。

【例子】

```python 
languages = ['Python', 'R', 'Matlab', 'C++']
for language in languages:
    print('I love', language)
print('Done!')

'''
I love Python
I love R
I love Matlab
I love C++
Done!
'''

for i, language in enumerate(languages, 2):
    print(i, 'I love', language)
print('Done!')

'''
2 I love Python
3 I love R
4 I love Matlab
5 I love C++
Done!
'''
```

##### 2.6 break语句

`break`语句可以**跳出当前所在层的循环**。

【例子】

```python
import random
secret = random.randint(1, 10) #[1,10]之间的随机数

while True:
    temp = input("不妨猜一下小哥哥现在心里想的是那个数字：")
    guess = int(temp)
    if guess > secret:
        print("大了，大了")
    else:
        if guess == secret:
            print("你这样懂小哥哥的心思啊？")
            print("哼，猜对也没有奖励！")
            break
        else:
            print("小了，小了")
print("游戏结束，不玩儿啦！")
```

##### 2.7 continue语句

`continue`**<u>终止本轮循环并开始下一轮循环</u>**。

【例子】

```python
for i in range(10):
    if i % 2 != 0:
        print(i)
        continue
    i += 2
    print(i)

# 2
# 1
# 4
# 3
# 6
# 5
# 8
# 7
# 10
# 9
```

###### continue语句和break语句的区别

> - continue语句只结束本次循环，而不是中止整个循环的执行
> - break语句则是结束整个循环过程，不再判断执行循环的条件是否成立
> - 注意：循环嵌套时，break和continue语句只影响包含他们的最内层循环，与外层循环无关

##### 2.8 pass语句

`pass` 语句的意思是“不做任何事”，**<u>如果你在需要有语句的地方不写任何语句，那么解释器会提示出错，而 `pass` 语句就是用来解决这些问题的</u>**。

【例子】

```python
def a_func():

# SyntaxError: unexpected EOF while parsing
```

【例子】

```python
def a_func():
    pass
```

`pass`是空语句，不做任何操作，只起到占位的作用，**其作用是为了保持程序结构的完整性**。尽管`pass`语句不做任何操作，但如果暂时不确定要在一个位置放上什么样的代码，可以先放置一个`pass`语句，让代码可以正常运行。

##### 2.9 推导式

- ###### **列表推导式**

```python
[ expr for value in collection [if condition] ]
```

【例子】

```python
x = [-4, -2, 0, 2, 4]
y = [a * 2 for a in x]
print(y)
# [-8, -4, 0, 4, 8]
```

【例子】

```python
x = [(i, i ** 2) for i in range(6)]
print(x)

# [(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]
```

【例子】

```python 
x = [i for i in range(100) if (i % 2) != 0 and (i % 3) == 0]
print(x)

# [3, 9, 15, 21, 27, 33, 39, 45, 51, 57, 63, 69, 75, 81, 87, 93, 99]
```

【例子】

```python
a = [(i, j) for i in range(0, 3) for j in range(0, 3)]
print(a)

# [(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2), (2, 0), (2, 1), (2, 2)]
```

【例子】

```python
x = [[i, j] for i in range(0, 3) for j in range(0, 3)]
print(x)
# [[0, 0], [0, 1], [0, 2], [1, 0], [1, 1], [1, 2], [2, 0], [2, 1], [2, 2]]

x[0][0] = 10
print(x)
# [[10, 0], [0, 1], [0, 2], [1, 0], [1, 1], [1, 2], [2, 0], [2, 1], [2, 2]]
```

【例子】

```python
a = [(i, j) for i in range(0, 3) if i < 1 for j in range(0, 3) if j > 1]
print(a)

# [(0, 2)]
```

- ###### **元组推导式**

```python
( expr for value in collection [if condition] )
```

【例子】

```python
a = (x for x in range(10))
print(a)

# <generator object <genexpr> at 0x0000025BE511CC48>

print(tuple(a))

# (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
```

- ##### **字典推导式**

```python
{ key_expr: value_expr for value in collection [if condition] }
```

【例子】

```python
b = {i: i % 2 == 0 for i in range(10) if i % 3 == 0}
print(b)
# {0: True, 3: False, 6: True, 9: False}
```

- **集合推导式**

```python
{ expr for value in collection [if condition] }
```

【例子】

```python
c = {i for i in [1, 2, 3, 4, 5, 5, 6, 4, 3, 2, 1]}
print(c)
# {1, 2, 3, 4, 5, 6}
```

- **其它**

```python 
d = 'i for i in "I Love Lsgogroup"'
print(d)
# i for i in "I Love Lsgogroup"

e = (i for i in range(10))
print(e)
# <generator object <genexpr> at 0x0000007A0B8D01B0>

print(next(e))  # 0
print(next(e))  # 1

for each in e:
    print(each, end=' ')

# 2 3 4 5 6 7 8 9

s = sum([i for i in range(101)])
print(s)  # 5050
s = sum((i for i in range(101)))
print(s)  # 5050
```