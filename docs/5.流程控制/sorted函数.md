sorted() 作为 Python 内置函数之一，其功能是对序列（列表、元组、字典、集合、还包括字符串）进行排序。

sorted() 函数的基本语法格式如下：
> list = sorted(iterable, key=None, reverse=False)  

其中，iterable 表示指定的序列，key 参数可以自定义排序规则；reverse 参数指定以升序（False，默认）还是降序（True）进行排序。sorted() 函数会返回一个排好序的列表。
> 注意，key 参数和 reverse 参数是可选参数，即可以使用，也可以忽略。

下面程序演示了 sorted() 函数的基本用法：
```python
#对列表进行排序
a = [5,3,4,2,1]
print(sorted(a))
#对元组进行排序
a = (5,4,3,1,2)
print(sorted(a))
#字典默认按照key进行排序
a = {4:1,5:2,3:3,2:6,1:8}
print(sorted(a.items()))
#对集合进行排序
a = {1,5,3,2,4}
print(sorted(a))
#对字符串进行排序
a = "51423"
print(sorted(a))
```
程序执行结果为：
```conlse
[1, 2, 3, 4, 5]
[1, 2, 3, 4, 5]
[(1, 8), (2, 6), (3, 3), (4, 1), (5, 2)]
[1, 2, 3, 4, 5]
['1', '2', '3', '4', '5']
```

再次强调，使用 sorted() 函数对序列进行排序， 并不会在原序列的基础进行修改，而是会重新生成一个排好序的列表。例如：
```python
#对列表进行排序
a = [5,3,4,2,1]
print(sorted(a))
#再次输出原来的列表 a
print(a)
```
程序执行结果为：
```conlse
[1, 2, 3, 4, 5]
[5, 3, 4, 2, 1]
```

显然，sorted() 函数不会改变所传入的序列，而是返回一个新的、排序好的列表。

除此之外，sorted(）函数默认对序列中元素进行升序排序，通过手动将其 reverse 参数值改为 True，可实现降序排序。例如：
```python
#对列表进行排序
a = [5,3,4,2,1]
print(sorted(a,reverse=True))
```
程序执行结果为：
```conlse
[5, 4, 3, 2, 1]
```


另外在调用 sorted() 函数时，还可传入一个 key 参数，它可以接受一个函数，该函数的功能是指定 sorted() 函数按照什么标准进行排序。例如：
```python
chars=['辰飞','辰飞IT教育','辰飞IT','辰飞IT职业教育']
#默认排序
print(sorted(chars))
#自定义按照字符串长度排序
print(sorted(chars,key=lambda x:len(x),reverse=True))
```
程序执行结果为：
```conlse
['辰飞', '辰飞IT', '辰飞IT教育', '辰飞IT职业教育']
['辰飞IT职业教育', '辰飞IT教育', '辰飞IT', '辰飞']
 ```

此程序中，使用了 lambda 表示式，参考lambda表达式