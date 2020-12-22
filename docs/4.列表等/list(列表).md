在实际开发中，经常需要将一组（不只一个）数据存储起来，以便后边的代码使用。你可能听说过数组（Array），它就可以把多个数据挨个存储到一起，通过数组下标可以访问数组中的每个元素。

需要明确的是，Python 中没有数组，但是加入了更加强大的列表。如果把数组看做是一个集装箱，那么 Python 的列表就是一个工厂的仓库。
大部分编程语言都支持数组，比如C语言、C++、Java、PHP、JavaScript 等。

从形式上看，列表会将所有元素都放在一对中括号[ ]里面，相邻元素之间用逗号,分隔，如下所示：
> [element1, element2, element3, ..., elementn]

格式中，element1 ~ elementn 表示列表中的元素，个数没有限制，只要是 Python 支持的数据类型就可以。

从内容上看，列表可以存储整数、小数、字符串、列表、元组等任何类型的数据，并且同一个列表中元素的类型也可以不同。比如说：

> ["http://doc-py.she-tech.cn/", 1, [2,3,4] , 3.0]

可以看到，列表中同时包含字符串、整数、列表、浮点数这些数据类型。
> 注意，在使用列表时，虽然可以将不同类型的数据放入到同一个列表中，但通常情况下不这么做，同一列表中只放入同一类型的数据，这样可以提高程序的可读性。

另外，在其它 Python 教程中，经常用 list 代指列表，这是因为列表的数据类型就是 list，通过 type() 函数就可以知道，例如：
```python
 print(type(["http://doc-py.she-tech.cn/", 1, [2,3,4] , 3.0] ))
```
结果
```consle
<class 'list'>
```

可以看到，它的数据类型为 list，就表示它是一个列表。
## Python创建列表
在 Python 中，创建列表的方法可分为两种，下面分别进行介绍。
**1) 使用 [ ] 直接创建列表**
使用[ ]创建列表后，一般使用=将它赋值给某个变量，具体格式如下：
> listname = [element1 , element2 , element3 , ... , elementn]

其中，listname 表示变量名，element1 ~ elementn 表示列表元素。

例如，下面定义的列表都是合法的：
```python
num = [1, 2, 3, 4, 5, 6, 7]
name = ["辰飞IT教育", "doc-py.she-tech.cn"]
program = ["C语言", "Python", "Java"]
```
另外，使用此方式创建列表时，列表中元素可以有多个，也可以一个都没有，例如：
> emptylist = [ ]

这表明，emptylist 是一个空列表。
**2) 使用 list() 函数创建列表**
除了使用[ ]创建列表外，Python 还提供了一个内置的函数 list()，使用它可以将其它数据类型转换为列表类型。例如：
```python
#将字符串转换成列表
list1 = list("hello")
print(list1)
#将元组转换成列表
tuple1 = ('Python', 'Java', 'C++', 'JavaScript')
list2 = list(tuple1)
print(list2)
#将字典转换成列表
dict1 = {'a':100, 'b':42, 'c':9}
list3 = list(dict1)
print(list3)
#将区间转换成列表
range1 = range(1, 6)
list4 = list(range1)
print(list4)
#创建空列表
print(list())
```python
运行结果：
```
```consle
['h', 'e', 'l', 'l', 'o']
['Python', 'Java', 'C++', 'JavaScript']
['a', 'b', 'c']
[1, 2, 3, 4, 5]
[]
```
## 访问列表元素
列表是 Python 序列的一种，我们可以使用索引（Index）访问列表中的某个元素（得到的是一个元素的值），也可以使用切片访问列表中的一组元素（得到的是一个新的子列表）。

使用索引访问列表元素的格式为：

> listname[i]

其中，listname 表示列表名字，i 表示索引值。列表的索引可以是正数，也可以是负数。

使用切片访问列表元素的格式为：
> listname[start : end : step]

其中，listname 表示列表名字，start 表示起始索引，end 表示结束索引，step 表示步长。

案例演示，请看下面代码：
```python
url = list("doc-py.she-tech.cn")
#使用索引访问列表中的某个元素
print(url[3])  #使用正数索引
print(url[-4])  #使用负数索引
#使用切片访问列表中的一组元素
print(url[9: 18])  #使用正数切片
print(url[9: 18: 3])  #指定步长
print(url[-6: -1])  #使用负数切片
```
运行结果：
```consle
-
h
['e', '-', 't', 'e', 'c', 'h', '.', 'c', 'n']
['e', 'e', '.']
['e', 'c', 'h', '.', 'c']
```

## Python删除列表
对于已经创建的列表，如果不再使用，可以使用del关键字将其删除。

实际开发中并不经常使用 del 来删除列表，因为 Python 自带的垃圾回收机制会自动销毁无用的列表，即使开发者不手动删除，Python 也会自动将其回收。

del 关键字的语法格式为：
> del listname

其中，listname 表示要删除列表的名称。

Python 删除列表实例演示：
```python
intlist = [1, 45, 8, 34]
print(intlist)
# 删除列表
del intlist
# 删除后再使用列表，这是会报错。因为列表已经不存在了
print(intlist)
```
运行结果：
```consle
[1, 45, 8, 34]
Traceback (most recent call last):
  File "C:/work/cf/python/TestEdu/t3.py", line 6, in <module>
    print(intlist)
NameError: name 'intlist' is not defined
```