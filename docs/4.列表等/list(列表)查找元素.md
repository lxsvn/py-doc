Python 列表（list）提供了 index() 和 count() 方法，它们都可以用来查找元素。
## index() 方法
index() 方法用来查找某个元素在列表中出现的位置（也就是索引），如果该元素不存在，则会导致 ValueError 错误，所以在查找之前最好使用 count() 方法判断一下。

index() 的语法格式为：
> listname.index(obj, start, end)

其中，listname 表示列表名称，obj 表示要查找的元素，start 表示起始位置，end 表示结束位置。

start 和 end 参数用来指定检索范围：
- start 和 end 可以都不写，此时会检索整个列表；
- 如果只写 start 不写 end，那么表示检索从 start 到末尾的元素；
- 如果 start 和 end 都写，那么表示检索 start 和 end 之间的元素。

index() 方法会返回元素所在列表中的索引值。

index() 方法使用举例：
```python
nums = [40, 36, 89, 2, 36, 100, 7, -20.5, -999]
#检索列表中的所有元素
print( nums.index(2) )
#检索3~7之间的元素
print( nums.index(100, 3, 7) )
#检索4之后的元素
print( nums.index(7, 4) )
#检索一个不存在的元素
print( nums.index(55) )
```
运行结果：
```consle
3
5
6
Traceback (most recent call last):
  File "C:/work/cf/python/TestEdu/t3.py", line 9, in <module>
    print( nums.index(55) )
ValueError: 55 is not in list
```

## count()方法
count() 方法用来统计某个元素在列表中出现的次数，基本语法格式为：
> listname.count(obj)

其中，listname 代表列表名，obj 表示要统计的元素。

如果 count() 返回 0，就表示列表中不存在该元素，所以 count() 也可以用来判断列表中的某个元素是否存在。

count() 用法示例：
```python
nums = [40, 36, 89, 2, 36, 100, 7, -20.5, 36]
#统计元素出现的次数
print("36出现了%d次" % nums.count(36))
#判断一个元素是否存在
if nums.count(100):
    print("列表中存在100这个元素")
else:
    print("列表中不存在100这个元素")
```
运行结果：
```consle
36出现了3次
列表中存在100这个元素
```