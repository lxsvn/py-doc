从形式上看，和字典类似，Python 集合会将所有元素放在一对大括号 {} 中，相邻元素之间用“,”分隔，如下所示：
> {element1,element2,...,elementn}

其中，elementn 表示集合中的元素，个数没有限制。

从内容上看，同一集合中，只能存储不可变的数据类型，包括整形、浮点型、字符串、元组，无法存储列表、字典、集合这些可变的数据类型，否则 Python 解释器会抛出 TypeError 错误。比如说：

例一

**集合无法存储 字典类型**：

```python
v = {{'a':1}}
```
运行报错
```conlse
Traceback (most recent call last):
  File "C:/work/cf/python/TestEdu/t3.py", line 1, in <module>
    v = {{'a':1}}
TypeError: unhashable type: 'dict'
```


例二

**集合无法存储 列表类型**：

```python
v = {[1,2,3]}
```
运行报错
```conlse
Traceback (most recent call last):
  File "C:/work/cf/python/TestEdu/t3.py", line 1, in <module>
    v = {[1,2,3]}
TypeError: unhashable type: 'list'
```

例三

**集合无法存储 集合类型**：

```python
v = {{1,2,3}}
```
运行报错
```conlse
Traceback (most recent call last):
  File "C:/work/cf/python/TestEdu/t3.py", line 1, in <module>
    v = {{1,2,3}}
TypeError: unhashable type: 'set'
```

并且需要注意的是，数据必须保证是唯一的，因为集合对于每种数据元素，只会保留一份。例如：
```python
v = {1,2,1,'c','c'}
print(v)
```
结果

```consle
{1, 2, 'c'}
```


> 由于 Python 中的 set 集合是无序的，所以每次输出时元素的排序顺序可能都不相同。
其实，Python 中有两种集合类型，一种是 set 类型的集合，另一种是 frozenset 类型的集合，它们唯一的区别是，set 类型集合可以做添加、删除元素的操作，而 forzenset 类型集合不行。本节先介绍 set 类型集合，后续章节再介绍 forzenset 类型集合。

## 创建set集合
Python 提供了 2 种创建 set 集合的方法，分别是使用 {} 创建和使用 set() 函数将列表、元组等类型数据转换为集合。

**1) 使用 {} 创建**

在 Python 中，创建 set 集合可以像列表、元素和字典一样，直接将集合赋值给变量，从而实现创建集合的目的，其语法格式如下：
> setname = {element1,element2,...,elementn}

其中，setname 表示集合的名称，起名时既要符合 Python 命名规范，也要避免与 Python 内置函数重名。

举个例子：
```python
a = {1,'c',1,(1,2,3),'c'}
print(a)
```
运行结果为：
```consle
{1, 'c', (1, 2, 3)}
```

**2) set()函数创建集合**

set() 函数为 Python 的内置函数，其功能是将字符串、列表、元组、range 对象等可迭代对象转换成集合。该函数的语法格式如下：
> setname = set(iteration)

其中，iteration 就表示字符串、列表、元组、range 对象等数据。

例如：
```python
set1 = set("doc-py.she-tech.cn/")
set2 = set(['w','z','t'])
set3 = set((1,2,3,4,5))
print("set1:",set1)
print("set2:",set2)
print("set3:",set3)
```
运行结果为：
```consle
set1: {'p', 'y', 'h', '/', 'n', '-', 'o', 's', 't', 'd', '.', 'e', 'c'}
set2: {'w', 't', 'z'}
set3: {1, 2, 3, 4, 5}
```

注意，如果要创建空集合，只能使用 set() 函数实现。因为直接使用一对 {}，Python 解释器会将其视为一个空字典。
## 访问set集合元素
由于集合中的元素是无序的，因此无法向列表那样使用下标访问元素。Python 中，访问集合元素最常用的方法是使用循环结构，将集合中的数据逐一读取出来。

例如：
```python
a = {1,'c',1,(1,2,3),'c'}
for ele in a:
    print(ele,end=' ')
```
运行结果为：
```consle
1 c (1, 2, 3)
```

## 删除set集合
和其他序列类型一样，手动函数集合类型，也可以使用 del() 语句，例如：
```python
a = {1,'c',1,(1,2,3),'c'}
print(a)
del(a)
print(a)
```
运行结果为：

```consle
{1, 'c', (1, 2, 3)}
Traceback (most recent call last):
  File "C:/work/cf/python/TestEdu/t3.py", line 4, in <module>
    print(a)
NameError: name 'a' is not defined
```


> Python set 集合最常用的操作是向集合中添加、删除元素，以及集合之间做交集、并集、差集等运算。后面实际运用会进行讲解。