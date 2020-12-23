reserved() 是 Pyton 内置函数之一，其功能是对于给定的序列（包括列表、元组、字符串以及 range(n) 区间），该函数可以返回一个逆序序列的迭代器（用于遍历该逆序序列）。

reserved() 函数的语法格式如下：
> reversed(seq)

其中，seq 可以是列表，元素，字符串以及 range() 生成的区间列表。

下面程序演示了 reversed() 函数的基本用法：
```python
#将列表进行逆序
print(list(reversed([1,2,3,4,5])))
#将元组进行逆序
print(list(reversed((1,2,3,4,5))))
#将字符串进行逆序
print(list(reversed("辰飞IT职业教育")))
#将 range() 生成的区间列表进行逆序
print(list(reversed(range(10))))
``
程序执行结果为：
```consle
[5, 4, 3, 2, 1]
[5, 4, 3, 2, 1]
['育', '教', '业', '职', 'T', 'I', '飞', '辰']
[9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

除了使用列表推导式的方式，还可以使用 list() 函数，将 reversed() 函数逆序返回的迭代器，直接转换成列表。例如：
```python
#将列表进行逆序
print(list(reversed([1,2,3,4,5])))
```
程序执行结果为：
```consle
[5, 4, 3, 2, 1]
```

再次强调，使用 reversed() 函数进行逆序操作，并不会修改原来序列中元素的顺序，例如：
```python
a = [1,2,3,4,5]
#将列表进行逆序
print(list(reversed(a)))
print("a =",a)
```
程序执行结果为：
```conlse
[5, 4, 3, 2, 1]
a = [1, 2, 3, 4, 5]
```