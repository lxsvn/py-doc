实际开发中，经常需要对 Python 列表进行更新，包括向列表中添加元素、修改表中元素以及删除元素。本节先来学习如何向列表中添加元素。

《什么事序列》一节告诉我们，使用+运算符可以将多个序列连接起来；列表是序列的一种，所以也可以使用+进行连接，这样就相当于在第一个列表的末尾添加了另一个列表。

请看下面的演示：
```python
language = ["Python", "C++", "Java"]
birthday = [1991, 1998, 1995]
info = language + birthday
print("language =", language)
print("birthday =", birthday)
print("info =", info)
```
运行结果：
```consle
language = ['Python', 'C++', 'Java']
birthday = [1991, 1998, 1995]
info = ['Python', 'C++', 'Java', 1991, 1998, 1995]
```

从运行结果可以发现，使用+会生成一个新的列表，原有的列表不会被改变。

+更多的是用来拼接列表，而且执行效率并不高，如果想在列表中插入元素，应该使用下面几个专门的方法。
## append()方法
append() 方法用于在列表的末尾追加元素，该方法的语法格式如下：
> listname.append(obj)

其中，listname 表示要添加元素的列表；obj 表示到添加到列表末尾的数据，它可以是单个元素，也可以是列表、元组等。

请看下面的演示：
```python
l = ['Python', 'C++', 'Java']
#追加元素
l.append('PHP')
print(l)
#追加元组，整个元组被当成一个元素
t = ('JavaScript', 'C#', 'Go')
l.append(t)
print(l)
#追加列表，整个列表也被当成一个元素
l.append(['Ruby', 'SQL'])
print(l)
```
运行结果为：
```consle
['Python', 'C++', 'Java', 'PHP']
['Python', 'C++', 'Java', 'PHP', ('JavaScript', 'C#', 'Go')]
['Python', 'C++', 'Java', 'PHP', ('JavaScript', 'C#', 'Go'), ['Ruby', 'SQL']]
```

可以看到，当给 append() 方法传递列表或者元组时，此方法会将它们视为一个整体，作为一个元素添加到列表中，从而形成包含列表和元组的新列表。
## extend()方法
extend() 和 append() 的不同之处在于：extend() 不会把列表或者元组视为一个整体，而是把它们包含的元素逐个添加到列表中。

extend() 方法的语法格式如下：
> listname.extend(obj)

其中，listname 指的是要添加元素的列表；obj 表示到添加到列表末尾的数据，它可以是单个元素，也可以是列表、元组等，但不能是单个的数字。

请看下面的演示：
```python
l = ['Python', 'C++', 'Java']
#追加元素
l.extend('C')
print(l)
#追加元组，元祖被拆分成多个元素
t = ('JavaScript', 'C#', 'Go')
l.extend(t)
print(l)
#追加列表，列表也被拆分成多个元素
l.extend(['Ruby', 'SQL'])
print(l)
```
运行结果：
```consle
['Python', 'C++', 'Java', 'C']
['Python', 'C++', 'Java', 'C', 'JavaScript', 'C#', 'Go']
['Python', 'C++', 'Java', 'C', 'JavaScript', 'C#', 'Go', 'Ruby', 'SQL']
```

## insert()方法插入元素
append() 和 extend() 方法只能在列表末尾插入元素，如果希望在列表中间某个位置插入元素，那么可以使用 insert() 方法。

insert() 的语法格式如下：
> listname.insert(index , obj)

其中，index 表示指定位置的索引值。insert() 会将 obj 插入到 listname 列表第 index 个元素的位置。

当插入列表或者元组时，insert() 也会将它们视为一个整体，作为一个元素插入到列表中，这一点和 append() 是一样的。

请看下面的演示代码：
```python
l = ['Python', 'C++', 'Java']
#插入元素
l.insert(1, 'C')
print(l)
#插入元组，整个元祖被当成一个元素
t = ('C#', 'Go')
l.insert(2, t)
print(l)
#插入列表，整个列表被当成一个元素
l.insert(3, ['Ruby', 'SQL'])
print(l)
#插入字符串，整个字符串被当成一个元素
l.insert(0, "doc-py.she-tech.cn")
print(l)
```
输出结果为：
```consle
['Python', 'C', 'C++', 'Java']
['Python', 'C', ('C#', 'Go'), 'C++', 'Java']
['Python', 'C', ('C#', 'Go'), ['Ruby', 'SQL'], 'C++', 'Java']
['doc-py.she-tech.cn', 'Python', 'C', ('C#', 'Go'), ['Ruby', 'SQL'], 'C++', 'Java']
```

> 提示，insert() 主要用来在列表的中间位置插入元素，如果你仅仅希望在列表的末尾追加元素，那更建议使用 append() 和 extend()。