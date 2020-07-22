# Task01：变量、运算符、数据类型及位运算

[TOC]

### 一、运算符

##### 1.算术运算符

| 操作符 | 名称                      | 示例     |
| ------ | ------------------------- | -------- |
| `+`    | 加                        | `1 + 1`  |
| `-`    | 减                        | `2 - 1`  |
| `*`    | 乘                        | `3 * 4`  |
| `/`    | 除                        | `3 / 4`  |
| `//`   | **<u>整除（地板除）</u>** | `3 // 4` |
| `%`    | 取余                      | `3 % 4`  |
| `**`   | 幂                        | `2 ** 3` |

##### 2.比较运算符

| 操作符 | 名称     | 示例     |
| ------ | -------- | -------- |
| `>`    | 大于     | `2 > 1`  |
| `>=`   | 大于等于 | `2 >= 4` |
| `<`    | 小于     | `1 < 2`  |
| `<=`   | 小于等于 | `5 <= 2` |
| `==`   | 等于     | `3 == 4` |
| `!=`   | 不等于   | `3 != 5` |

【例子】

```python
print(2 > 1)  # True
print(2 >= 4)  # False
print(1 < 2)  # True
print(5 <= 2)  # False
print(3 == 4)  # False
print(3 != 5)  # True
```

##### 3.逻辑运算符

| 操作符 | 名称 | 示例                  |
| ------ | ---- | --------------------- |
| `and`  | 与   | `(3 > 2) and (3 < 5)` |
| `or`   | 或   | `(1 > 3) or (9 < 2)`  |
| `not`  | 非   | `not (2 > 1)`         |

【例子】

```python
print((3 > 2) and (3 < 5))  # True
print((1 > 3) or (9 < 2))  # False
print(not (2 > 1))  # False
```

##### 4.位运算符

| 操作符 | 名称     | 示例     |
| ------ | -------- | -------- |
| `~`    | 按位取反 | `~4`     |
| `&`    | 按位与   | `4 & 5`  |
| `|`    | 按位或   | `4 | 5`  |
| `^`    | 按位异或 | `4 ^ 5`  |
| `<<`   | 左移     | `4 << 2` |
| `>>`   | 右移     | `4 >> 2` |

```python
print(bin(4))  # 0b100
print(bin(5))  # 0b101
print(bin(~4), ~4)  # -0b101 -5
print(bin(4 & 5), 4 & 5)  # 0b100 4
print(bin(4 | 5), 4 | 5)  # 0b101 5
print(bin(4 ^ 5), 4 ^ 5)  # 0b1 1
print(bin(4 << 2), 4 << 2)  # 0b10000 16
print(bin(4 >> 2), 4 >> 2)  # 0b1 1
```



###### 关于~4结果为-5的个人理解：

> 1. 4作为正数，补码为0100
> 2. 取反操作后，为1011（这也是一种补码形式）
> 3. 补码=反码+1，因此反码=1010
> 4. 取反之后得到0101，值为5
> 5. 符号位看补码（反码应该也可以，均为1，表示负数）
> 6. 答案为-5

异或：

```python
0^0 #0 
1^0 #1
0^1 #1
1^1 #0
```



##### 5.三元运算符

```python
x, y = 4, 5
if x < y:
    small = x
else:
    small = y

print(small)  # 4
```

使用一条语句完成以上条件判断和赋值操作

```python
x,y=4,5
small=x if x<y else y
print(small)
```

##### 6.其他运算符

| 操作符   | 名称   | 示例                         |
| -------- | ------ | ---------------------------- |
| `in`     | 存在   | `'A' in ['A', 'B', 'C']`     |
| `not in` | 不存在 | `'h' not in ['A', 'B', 'C']` |
| `is`     | 是     | `"hello" is "hello"`         |
| `is not` | 不是   | `"hello" is not "hello"`     |

例1：比较的两个变量均指向不可变类型

```python
a = "hello"
b = "hello"
print(a is b, a == b)  # True True
print(a is not b, a != b)  # False False
```

例2：比较的两个变量均指向可变类型(元组是不是可变类型？)

```python
a = ["hello"]
b = ["hello"]
print(a is b, a == b)  # False True
print(a is not b, a != b)  # True False
```

扩展：

```python
a = ("hello")
b = ("hello")
print(a is b, a == b)  # True True
print(a is not b, a != b)  # False False
```

```python
a = {"hello"}
b = {"hello"}
print(a is b, a == b)  # False True
print(a is not b, a != b)  # True False
```

##### **注意**

> - is, is not 对比的是两个变量的内存地址
> - ==, != 对比的是两个变量的值
> - 比较的两个变量，指向的都是地址不可变的类型（str等），那么is，is not 和 ==，！= 是完全等价的。
> - 对比的两个变量，指向的是**<u>*地址可变的类型（list，dict，tuple等）*</u>**，则两者是有区别的。



例3：

```python
print(-3 ** 2)  # -9
print(3 ** -2)  # 0.1111111111111111
print(1 << 3 + 2 & 7)  # 0
print(-3 * 2 + 5 / -2 - 4)  # -12.5
print(3 < 4 and 4 < 5)  # True
```

**运算符的优先级**

> - 一元运算符优于二元运算符。例如`3 ** -2`等价于`3 ** (-2)`。
> - **<u>先算术运算，后移位运算，最后位运算</u>**。例如 `1 << 3 + 2 & 7`等价于 `(1 << (3 + 2)) & 7`。
> - 逻辑运算最后结合。例如`3 < 4 and 4 < 5`等价于`(3 < 4) and (4 < 5)`。



### 二、变量和赋值

> - 在使用变量之前，需要对其先赋值。
> - 变量名可以包括字母、数字、下划线、但**<u>变量名不能以数字开头</u>**。
> - Python 变量名是大小写敏感的，foo != Foo



### 三、数据类型与转换

##### 3.1 整形

Python 里面万物皆对象（object），整型也不例外，只要是对象，就有相应的属性 （attributes） 和方法（methods）。

```python
b = dir(int)
print(b)

# ['__abs__', '__add__', '__and__', '__bool__', '__ceil__', '__class__',
# '__delattr__', '__dir__', '__divmod__', '__doc__', '__eq__',
# '__float__', '__floor__', '__floordiv__', '__format__', '__ge__',
# '__getattribute__', '__getnewargs__', '__gt__', '__hash__',
# '__index__', '__init__', '__init_subclass__', '__int__', '__invert__',
# '__le__', '__lshift__', '__lt__', '__mod__', '__mul__', '__ne__',
# '__neg__', '__new__', '__or__', '__pos__', '__pow__', '__radd__',
# '__rand__', '__rdivmod__', '__reduce__', '__reduce_ex__', '__repr__',
# '__rfloordiv__', '__rlshift__', '__rmod__', '__rmul__', '__ror__',
# '__round__', '__rpow__', '__rrshift__', '__rshift__', '__rsub__',
# '__rtruediv__', '__rxor__', '__setattr__', '__sizeof__', '__str__',
# '__sub__', '__subclasshook__', '__truediv__', '__trunc__', '__xor__',
# 'bit_length', 'conjugate', 'denominator', 'from_bytes', 'imag',
# 'numerator', 'real', 'to_bytes']
```

看个`bit_length()`的例子。

【例子】找到一个整数的二进制表示，再返回其长度。

```python
a = 1031
print(bin(a))  # 0b10000000111
print(a.bit_length())  # 11
```

##### 3.2 浮点型

有时候我们想保留浮点型的小数点后 `n` 位。可以用 `decimal` 包里的 `Decimal` 对象和 `getcontext()` 方法来实现。

```python
import decimal
from decimal import Decimal
```

【例子】`getcontext()` 显示了 `Decimal` 对象的默认精度值是 28 位 (`prec=28`)。

```python
a = decimal.getcontext()
print(a)

# Context(prec=28, rounding=ROUND_HALF_EVEN, Emin=-999999, Emax=999999,
# capitals=1, clamp=0, flags=[], 
# traps=[InvalidOperation, DivisionByZero, Overflow])
b = Decimal(1) / Decimal(3)
print(b)

# 0.3333333333333333333333333333
```

【例子】使 1/3 保留 4 位，用 `getcontext().prec` 来调整精度。

```python
decimal.getcontext().prec = 4
c = Decimal(1) / Decimal(3)
print(c)

# 0.3333
```

##### 3.3 布尔型

除了直接给变量赋值 `True` 和 `False`，还可以用 `bool(X)` 来创建变量，其中 `X` 可以是

> - 基本类型：整型、浮点型、布尔型
> - 容器类型：**<u>字符串、元组、列表、字典和集合</u>**

【例子】`bool` 作用在基本类型变量：`X` 只要不是整型 `0`、浮点型 `0.0`，`bool(X)` 就是 `True`，其余就是 `False`。

```python
print(type(0), bool(0), bool(1))
# <class 'int'> False True

print(type(10.31), bool(0.00), bool(10.31))
# <class 'float'> False True

print(type(True), bool(False), bool(True))
# <class 'bool'> False True
```

【例子】`bool` 作用在容器类型变量：`X` 只要不是空的变量，`bool(X)` 就是 `True`，其余就是 `False`。

```python
print(type(''), bool(''), bool('python'))
# <class 'str'> False True

print(type(()), bool(()), bool((10,)))
# <class 'tuple'> False True

print(type([]), bool([]), bool([1, 2]))
# <class 'list'> False True

print(type({}), bool({}), bool({'a': 1, 'b': 2}))
# <class 'dict'> False True

print(type(set()), bool(set()), bool({1, 2}))
# <class 'set'> False True
```

##### **总结**

确定`bool(X)` 的值是 `True` 还是 `False`，就看 `X` 是不是空，空的话就是 `False`，不空的话就是 `True`。

- **<u>对于数值变量，`0`, `0.0` 都可认为是空的。</u>**
- 对于容器变量，里面没元素就是空的。

##### 3.4 获取类型信息

- `type(object)` 获取类型信息

- `isinstance(object, classinfo)` 判断一个对象是否是一个已知的类型。

【例子】

```python
print(isinstance(1, int))  # True
print(isinstance(5.2, float))  # True
print(isinstance(True, bool))  # True
print(isinstance('5.2', str))  # True
```

注：

- `type()` 不会认为子类是一种父类类型，不考虑继承关系。
- `isinstance()` **<u>会认为子类是一种父类类型，考虑继承关系</u>**。

**<u>如果要判断两个类型是否相同推荐使用</u>** `isinstance()`。

##### 3.5 类型转换

- 转换为整型 `int(x, base=10)`

- 转换为字符串 `str(object='')`

- 转换为浮点型 `float(x)`

  其中，**<u>base=10表示对于x（通常是一个字符串）按照10进制转换成整数</u>**

```python
int('101',base=2) #5
int('101',base=8) #65
int('101',base=16) #257
```

【例子】

```python
print(int('520'))  # 520
print(int(520.52))  # 520
print(float('520.52'))  # 520.52
print(float(520))  # 520.0
print(str(10 + 10))  # 20
print(str(10.1 + 5.2))  # 15.3
```



### 四、位运算

##### 4.1 原码、反码和补码

二进制有三种不同的表示形式：原码、反码和补码，**<u>计算机内部使用补码来表示</u>**。

- 原码：其实就是二进制表示（注意，有一位符号位）

```sql
00 00 00 11 -> 3
10 00 00 11 -> -3
```

- 反码：**<u>正数的反码就是原码，负数的反码是符号位不变，其余位取反（对应正数按位取反）</u>**

```sql
00 00 00 11 -> 3
11 11 11 00 -> -3
```

- 补码：正数的补码就是原码，负数的补码是反码+1

```sql
00 00 00 11 -> 3
11 11 11 01 -> -3
```

- 符号位：**<u>最高位为符号位，0表示正数，1表示负数。在位运算中符号位也参与运算。</u>**

##### 4.2 按位非操作~

```sql
~1=0
~0=1
```

~把num的**<u>*补码中的0和1全部取反*</u>**（0变为1，1变为0）有符号整数的符号位在~运算中同样会取反。

```sql
00 00 01 01 -> 5
~
---
11 11 10 10 -> -6
11 11 10 11 -> -5
~
---
00 00 01 00 -> 4
```



------

------>按位与、或操作略

------

##### 4.3 按位异或操作

只有两个对应位不同是才为1

```sql
00 00 01 01 -> 5
^
00 00 01 10 -> 6
---
00 00 00 11 -> 3
```

异或操作性质：**<u>*满足交换律和结合律*</u>**

```sql
A: 00 00 11 00
B: 00 00 01 11
A^B: 00 00 10 11
B^A: 00 00 10 11
A^A: 00 00 00 00
A^0: 00 00 11 00
A^B^A: = A^A^B = B = 00 00 01 11
```

##### 4.4 按位左移和右移操作

左移：

```sql
00 00 10 11 -> 11
11 << 3
---
01 01 10 00 -> 88
```

右移：

```sql
00 00 10 11 -> 11
11 >> 2
---
00 00 00 10 -> 2
```

##### 4.5 利用位运算实现快速计算

- 通过<<，>>快速计算2的倍数问题

```sql
n << 1 -> 计算 n*2
n >> 1 -> 计算 n/2，负奇数的运算不可用
n << m -> 计算 n*(2^m)，即乘以2的m次方
n >> m -> 计算 n/(2^m)，即除以2的m次方
1 << n -> 计算 2^n
```

- 通过 ^ 快速交换两个整数（以a=2（0010），b=10（1010）为例）

```sql
a ^= b   #a=1000
b ^= a   #b=0010
a ^= b   #a=1010
```

- **<u>通过a&(-a)快速获取a的最后为1位置的整数</u>**

  ```sql
  00 00 01 01 -> 5
  &
  11 11 10 11 -> -5
  ---
  00 00 00 01 -> 1
  
  00 00 11 10 -> 14
  &
  11 11 00 10 -> -14
  ---
  00 00 00 10 -> 2
  ```

<u>*个人觉得，例子中的负数是按照补码的形式*</u>

##### 4.6 利用位运算实现整数集合

一个数的二进制表示可以看作是一个集合（0表示不在集合中，1表示在集合中）

比如集合{1,3,4,8}可以表示成 01 00 01 10 10 ，而对应的位运算也就可以看作是对集合进行的操作。

**元素与集合的操作：**

```python
a | (1<<i)  -> 把 i 插⼊入到集合中
a & ~(1<<i) -> 把 i 从集合中删除
a & (1<<i)  -> 判断 i 是否属于该集合(零不属于，非零属于)
```

集合之间的操作：

```python
a 补   -> ~a
a 交 b -> a & b
a 并 b -> a | b
a 差 b -> a&(~b)
```



**<u>*整数在内存中是以补码的形式存在*</u>**的，输出自然也是按照补码输出。

但我们看一下python的bin()输出。

```python
print(bin(3)) # 0b11
print(bin(-3))  # -0b11

print(bin(-3 & 0xffffffff))
# 0b11111111111111111111111111111101
print(bin(0xfffffffd))
# 0b11111111111111111111111111111101
print(0xfffffffd) # 4294967293
```

从结果看出：

> 1. python中的bin一个负数（十进制表示），输出的是他的原码的二进制表示加上个负号，巨坑
> 2. python中的整形是以补码形式存储
> 3. **<u>python中整形是不限制长度的不会超范围溢出</u>**

所以为了获得负数（十进制表示）的补码，需要<u>**手动将其和十六进制数0xffffffff进行按位与操作，再交给bin()进行输出，得到的才是负数的补码表示**</u>。

