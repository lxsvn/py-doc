Python 字典（dict）是一种无序的、可变的序列，它的元素以“键值对（key-value）”的形式存储。相对地，列表（list）和元组（tuple）都是有序的序列，它们的元素在底层是挨着存放的。

字典类型是 Python 中唯一的映射类型。“映射”是数学中的术语，简单理解，它指的是元素之间相互对应的关系，即通过一个元素，可以唯一找到另一个元素。如图 1 所示。

<div class='img_content'>
    <img  src="../imgs/4.3.gif" />
    <span>图 1 映射关系示意图</span>
</div>



字典中，习惯将各元素对应的索引称为键（key），各个键对应的元素称为值（value），键及其关联的值称为“键值对”。

字典类型很像学生时代常用的新华字典。我们知道，通过新华字典中的音节表，可以快速找到想要查找的汉字。其中，字典里的音节表就相当于字典类型中的键，而键对应的汉字则相当于值。

总的来说，字典类型所具有的主要特征如表 1 所示。




|  主要特征   | 解释  | 
|  ----  | ----  |
|通过键而不是通过索引来读取元素	|字典类型有时也称为关联数组或者散列表（hash）。它是通过键将一系列的值联系起来的，这样就可以通过键从字典中获取指定项，但不能通过索引来获取。|
|字典是任意数据类型的无序集合	|和列表、元组不同，通常会将索引值 0 对应的元素称为第一个元素，而字典中的元素是无序的。|
|字典是可变的，并且可以任意嵌套	|字典可以在原处增长或者缩短（无需生成一个副本），并且它支持任意深度的嵌套，即字典存储的值也可以是列表或其它的字典。|
|字典中的键必须唯一	|字典中，不支持同一个键出现多次，否则只会保留最后一个键值对。|
|字典中的键必须不可变	|字典中每个键值对的键是不可变的，只能使用数字、字符串或者元组，不能使用列表。|

表 1 Python 字典特征

> Python 中的字典类型相当于 Java 或者 C++ 中的 Map 对象。


和列表、元组一样，字典也有它自己的类型。Python 中，字典的数据类型为 dict，通过 type() 函数即可查看：
```python
# a是一个字典类型
a = {'one': 1, 'two': 2, 'three': 3}
print(type(a))
```
结果

```consle
<class 'dict'>
```

## 创建字典
创建字典的方式有很多，下面一一做介绍。

**1) 使用 { } 创建字典**

由于字典中每个元素都包含两部分，分别是键（key）和值（value），因此在创建字典时，键和值之间使用冒号:分隔，相邻元素之间使用逗号,分隔，所有元素放在大括号{ }中。

使用{ }创建字典的语法格式如下：
> dictname = {'key':'value1', 'key2':'value2', ..., 'keyn':valuen}

其中 dictname 表示字典变量名，keyn : valuen 表示各个元素的键值对。需要注意的是，同一字典中的各个键必须唯一，不能重复。

如下代码示范了使用花括号语法创建字典：
```python
#使用字符串作为key
scores = {'数学': 95, '英语': 92, '语文': 84}
print(scores)
#使用元组和数字作为key
dict1 = {(20, 30): 'great', 30: [1,2,3]}
print(dict1)
#创建空元组
dict2 = {}
print(dict2)
```
运行结果为：
```consle
{'数学': 95, '英语': 92, '语文': 84}
{(20, 30): 'great', 30: [1, 2, 3]}
{}
```

可以看到，字典的键可以是整数、字符串或者元组，只要符合唯一和不可变的特性就行；字典的值可以是 Python 支持的任意数据类型。
**2) 通过 fromkeys() 方法创建字典**
Python 中，还可以使用 dict 字典类型提供的 fromkeys() 方法创建带有默认值的字典，具体格式为：
> dictname = dict.fromkeys(list，value=None)

其中，list 参数表示字典中所有键的列表（list）；value 参数表示默认值，如果不写，则为空值 None。

请看下面的例子：
```python
knowledge = ['语文', '数学', '英语']
scores = dict.fromkeys(knowledge, 60)
print(scores)
```
运行结果为：
```consle
{'语文': 60, '英语': 60, '数学': 60}
```

可以看到，knowledge 列表中的元素全部作为了 scores 字典的键，而各个键对应的值都是 60。这种创建方式通常用于初始化字典，设置 value 的默认值。
**3) 通过 dict() 映射函数创建字典**
通过 dict() 函数创建字典的写法有多种，表 2 罗列出了常用的几种方式，它们创建的都是同一个字典 a。

|  创建格式   | 注意事项  | 
|  ----  | ----  |
|a = dict(str1=value1, str2=value2, str3=value3)	|str 表示字符串类型的键，value 表示键对应的值。使用此方式创建字典时，字符串不能带引号。|
|#方式1 <br/>demo = [('two',2), ('one',1), ('three',3)] <br/>#方式2 <br/>demo = [['two',2], ['one',1],['three',3]]<br/>#方式3<br/>demo = (('two',2), ('one',1), ('three',3))<br/>#方式4<br/>demo = (['two',2], ['one',1], ['three',3])<br/>a = dict(demo)	|向 dict() 函数传入列表或元组，而它们中的元素又各自是包含 2 个元素的列表或元组，其中第一个元素作为键，第二个元素作为值。|
|keys = ['one', 'two', 'three'] #还可以是字符串或元组<br/>values = [1, 2, 3] #还可以是字符串或元组<br/>a = dict( zip(keys, values) )	| 通过应用 dict() 函数和 zip() 函数，可将前两个列表转换为对应的字典。|

表 2 dict() 函数创建字典

> 注意，无论采用以上哪种方式创建字典，字典中各元素的键都只能是字符串、元组或数字，不能是列表。列表是可变的，不能作为键。

如果不为 dict() 函数传入任何参数，则代表创建一个空的字典，例如：
```python
# 创建空的字典
d = dict()
print(d)
```
运行结果为：
```consle
{}
```

## 访问字典
列表和元组是通过下标来访问元素的，而字典不同，它通过键来访问对应的值。因为字典中的元素是无序的，每个元素的位置都不固定，所以字典也不能像列表和元组那样，采用切片的方式一次性访问多个元素。

Python 访问字典元素的具体格式为：
> dictname[key]

其中，dictname 表示字典变量的名字，key 表示键名。注意，键必须是存在的，否则会抛出异常。

请看下面的例子：
```python
tup = (['two',26], ['one',88], ['three',100], ['four',-59])
dic = dict(tup)
print(dic['one'])  #键存在
print(dic['five'])  #键不存在
```
运行结果：
```consle
88
Traceback (most recent call last):
  File "C:/work/cf/python/TestEdu/t3.py", line 4, in <module>
    print(dic['five'])  #键不存在
KeyError: 'five'
```

除了上面这种方式外，Python 更推荐使用 dict 类型提供的 get() 方法来获取指定键对应的值。当指定的键不存在时，get() 方法不会抛出异常。

*get() 方法*
> dictname.get(key[,default])

其中，dictname 表示字典变量的名字；key 表示指定的键；default 用于指定要查询的键不存在时，此方法返回的默认值，如果不手动指定，会返回 None。

get() 使用示例：
```python
a = dict(two=0.65, one=88, three=100, four=-59)
print( a.get('one') )
```
运行结果：
```consle
88
```


注意，当键不存在时，get() 返回空值 None，如果想明确地提示用户该键不存在，那么可以手动设置 get() 的第二个参数，例如：
```python
a = dict(two=0.65, one=88, three=100, four=-59)
print( a.get('five', '该键不存在') )
```
运行结果：
```consle
该键不存在
```

## 删除字典
和删除列表、元组一样，手动删除字典也可以使用 del 关键字，例如：
```python
a = dict(two=0.65, one=88, three=100, four=-59)
print(a)
del a
print(a)
```
运行结果：
```conlse
{'two': 0.65, 'one': 88, 'three': 100, 'four': -59}
Traceback (most recent call last):
  File "C:/work/cf/python/TestEdu/t3.py", line 4, in <module>
    print(a)
NameError: name 'a' is not defined
```

> Python 自带垃圾回收功能，会自动销毁不用的字典，所以一般不需要通过 del 来手动删除。