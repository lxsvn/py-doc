我们知道，Python 字典的数据类型为 dict，我们可使用 dir(dict) 来查看该类型包含哪些方法，例如：
```python
print(dir(dict))
```
结果
```consle
['clear', 'copy', 'fromkeys', 'get', 'items', 'keys', 'pop', 'popitem', 'setdefault', 'update', 'values']
```

这些方法中，fromkeys() 和 get() 的用法已经进行了介绍，这里不再赘述，本节只给大家介绍剩下的方法。
## keys()、values() 和 items() 方法
将这三个方法放在一起介绍，是因为它们都用来获取字典中的特定数据：
- keys() 方法用于返回字典中的所有键（key）；
- alues() 方法用于返回字典中所有键对应的值（value）；
- items() 用于返回字典中所有的键值对（key-value）。

请看下面的例子：
```python
scores = {'数学': 95, '语文': 89, '英语': 90}
print(scores.keys())
print(scores.values())
print(scores.items())
```
运行结果：
```consle
dict_keys(['数学', '语文', '英语'])
dict_values([95, 89, 90])
dict_items([('数学', 95), ('语文', 89), ('英语', 90)])
```

可以发现，keys()、values() 和 items() 返回值的类型分别为 dict_keys、dict_values 和 dict_items。

需要注意的是，在 Python 2.x 中，上面三个方法的返回值都是列表（list）类型。但在 Python 3.x 中，它们的返回值并不是我们常见的列表或者元组类型，因为 Python 3.x 不希望用户直接操作这几个方法的返回值。

在 Python 3.x 中如果想使用这三个方法返回的数据，一般有下面两种方案：

**1) 使用 list() 函数，将它们返回的数据转换成列表**

例如：
```python
a = {'数学': 95, '语文': 89, '英语': 90}
b = list(a.keys())
print(b)
```
运行结果为：
```consle
['数学', '语文', '英语']
```


**2) 使用 for in 循环遍历它们的返回值**

例如：
```python
a = {'数学': 95, '语文': 89, '英语': 90}
for k in a.keys():
    print(k,end=' ')
print("\n---------------")
for v in a.values():
    print(v,end=' ')
print("\n---------------")
for k,v in a.items():
    print("key:",k," value:",v)
```
运行结果为：
```consle
数学 语文 英语
---------------
95 89 90
---------------
key: 数学  value: 95
key: 语文  value: 89
key: 英语  value: 90
```

## copy() 方法
copy() 方法返回一个字典的拷贝，也即返回一个具有相同键值对的新字典，例如：
```python
a = {'one': 1, 'two': 2, 'three': [1,2,3]}
b = a.copy()
print(b)
```
运行结果为：
```consle
{'one': 1, 'two': 2, 'three': [1, 2, 3]}
```

可以看到，copy() 方法将字典 a 的数据全部拷贝给了字典 b。

> 注意，copy() 方法所遵循的拷贝原理，既有深拷贝，也有浅拷贝。拿拷贝字典 a 为例，copy() 方法只会对最表层的键值对进行深拷贝，也就是说，它会再申请一块内存用来存放 {'one': 1, 'two': 2, 'three': []}；而对于某些列表类型的值来说，此方法对其做的是浅拷贝，也就是说，b 中的 [1,2,3] 的值不是自己独有，而是和 a 共有。

请看下面的例子：
```python
a = {'one': 1, 'two': 2, 'three': [1,2,3]}
b = a.copy()
#向 a 中添加新键值对，由于b已经提前将 a 所有键值对都深拷贝过来，因此 a 添加新键值对，不会影响 b。
a['four']=100
print(a)
print(b)
#由于 b 和 a 共享[1,2,3]（浅拷贝），因此移除 a 中列表中的元素，也会影响 b。
a['three'].remove(1)
print(a)
print(b)
```
运行结果为：
```consle
{'one': 1, 'two': 2, 'three': [1, 2, 3], 'four': 100}
{'one': 1, 'two': 2, 'three': [1, 2, 3]}
{'one': 1, 'two': 2, 'three': [2, 3], 'four': 100}
{'one': 1, 'two': 2, 'three': [2, 3]}
```

从运行结果不难看出，对 a 增加新键值对，b 不变；而修改 a 某键值对中列表内的元素，b也会相应改变。
## update() 方法

update() 方法可以使用一个字典所包含的键值对来更新己有的字典。

在执行 update() 方法时，如果被更新的字典中己包含对应的键值对，那么原 value 会被覆盖；如果被更新的字典中不包含对应的键值对，则该键值对被添加进去。

请看下面的代码：
```python
a = {'one': 1, 'two': 2, 'three': 3}
a.update({'one':4.5, 'four': 9.3})
print(a)
```
运行结果为：
```conlse
{'one': 4.5, 'two': 2, 'three': 3, 'four': 9.3}
```

从运行结果可以看出，由于被更新的字典中已包含 key 为“one”的键值对，因此更新时该键值对的 value 将被改写；而被更新的字典中不包含 key 为“four”的键值对，所以更新时会为原字典增加一个新的键值对。
## pop() 和 popitem() 方法

- pop():删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。 否则，返回default值。
- popitem():删除并返回字典中的最后一对键和值。

> dictname.pop(key)

> dictname.popitem()

其中，dictname 表示字典名称，key 表示键。

下面的代码演示了两个函数的用法：
```python
a = {'数学': 95, '语文': 89, '英语': 90, '化学': 83, '生物': 98, '物理': 89}
print(a)
a.pop('化学')
print(a)
a.popitem()
print(a)
```
运行结果：
```conlse
{'数学': 95, '语文': 89, '英语': 90, '化学': 83, '生物': 98, '物理': 89}
{'数学': 95, '语文': 89, '英语': 90, '生物': 98, '物理': 89}
{'数学': 95, '语文': 89, '英语': 90, '生物': 98}
```

## setdefault() 方法
setdefault() 方法用来返回某个 key 对应的 value，其语法格式如下：
dictname.setdefault(key, defaultvalue)

说明，dictname 表示字典名称，key 表示键，defaultvalue 表示默认值（可以不写，不写的话是 None）。

当指定的 key 不存在时，setdefault() 会先为这个不存在的 key 设置一个默认的 defaultvalue，然后再返回 defaultvalue。

也就是说，setdefault() 方法总能返回指定 key 对应的 value：
- 如果该 key 存在，那么直接返回该 key 对应的 value；
- 如果该 key 不存在，那么先为该 key 设置默认的 defaultvalue，然后再返回该 key 对应的 defaultvalue。

请看下面的代码：
```python
a = {'数学': 95, '语文': 89, '英语': 90}
print(a)
#key不存在，指定默认值
a.setdefault('物理', 94)
print(a)
#key不存在，不指定默认值
a.setdefault('化学')
print(a)
#key存在，指定默认值
a.setdefault('数学', 100)
print(a)
```
运行结果为：
```conlse
{'数学': 95, '语文': 89, '英语': 90}
{'数学': 95, '语文': 89, '英语': 90, '物理': 94}
{'数学': 95, '语文': 89, '英语': 90, '物理': 94, '化学': None}
{'数学': 95, '语文': 89, '英语': 90, '物理': 94, '化学': None}
```