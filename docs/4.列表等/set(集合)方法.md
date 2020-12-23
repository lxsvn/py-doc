前面学习了 set 集合，本节来一一学习 set 类型提供的方法。首先，通过 dir(set) 命令可以查看它有哪些方法：
```python
print(dir(set))
```
结果
```consle
['add', 'clear', 'copy', 'difference', 'difference_update', 'discard', 'intersection', 'intersection_update', 'isdisjoint', 'issubset', 'issuperset', 'pop', 'remove', 'symmetric_difference', 'symmetric_difference_update', 'union', 'update']
```


各个方法的具体语法结构及功能如表 1 所示。


|方法名	|语法格式	|功能	|实例|
|----|----|----|----|
|add()|	set1.add()	|向 set1 集合中添加数字、字符串、元组或者布尔类型	|>>> set1 = {1,2,3} <br> >>> set1.add((1,2))  <br>>>> set1 <br>{(1, 2), 1, 2, 3}|
|clear()|	set1.clear()	|清空 set1 集合中所有元素|	>>> set1 = {1,2,3} <br> >>> set1.clear() <br> >>> set1set() <br> <br> set()才表示空集合，{}表示的是空字典|
|copy()	|set2 = set1.copy()	|拷贝 set1 集合给 set2|	>>> set1 = {1,2,3} <br> >>> set2 = set1.copy() <br> >>> set1.add(4) <br> >>> set1 <br> {1, 2, 3, 4} <br> >>> set1 <br> {1, 2, 3}|
|difference()	| set3 = set1.difference(set2)	|将 set1 中有而 set2 没有的元素给 set3	|>>> set1 = {1,2,3}<br>>>> set2 = {3,4}<br>>>> set3 = set1.difference(set2)<br>>>> set3<br>{1, 2}
|difference_update()|	set1.difference_update(set2)|	从 set1 中删除与 set2 相同的元素	|>>> set1 = {1,2,3}<br>>>> set2 = {3,4}<br>>>> set1.difference_update(set2)<br>>>> set1<br>{1, 2}
|discard()	|set1.discard(elem)	|删除 set1 中的 elem 元素	|>>> set1 = {1,2,3}<br>>>> set1.discard(2)<br>>>> set1<br>{1, 3}<br>>>> set1.discard(4)<br>{1, 3}|
|intersection()	|set3 = set1.intersection(set2)|	取 set1 和 set2 的交集给 set3|	>>> set1 = {1,2,3}<br>>>>set2 = {3,4}<br>>>> set3 = set1.intersection(set2)<br>>>> set3<br>{3}|
|intersection_update()|	set1.intersection_update(set2)|	取 set1和 set2 的交集，并更新给 set1	|>>> set1= {1,2,3}<br>>>> set2 = {3,4}<br>>>> set1.intersection_update(set2)<br>>>> set1<br>{3}|
|isdisjoint()|	set1.isdisjoint(set2)	|判断 set1 和 set2 是否没有交集，有交集返回 False；没有交集返回 True	|>>> set1 = {1,2,3}<br>>>> set2 = {3,4}<br>>>> set1.isdisjoint(set2)<br>False|
|issubset()	|set1.issubset(set2)	|判断 set1 是否是 set2 的子集|	>>> set1 = {1,2,3}<br>>>> set2 = {1,2}<br>>>> set1.issubset(set2)<br>False|
|issuperset()	|set1.issuperset(set2)	|判断 set2 是否是 set1 的子集|	>>> set1 = {1,2,3}<br>>>> set2 = {1,2}<br>>>> set1.issuperset(set2)<br>True|
|pop()|	a = set1.pop()	|取 set1 中一个元素，并赋值给 a	|>>> set1 = {1,2,3}<br>>>> a = set1.pop()<br>>>> set1<br>{2,3}<br>>>> a<br>1|
|remove()|	set1.remove(elem)|	移除 set1 中的 elem 元素|	>>> set1 = {1,2,3}<br>>>> set1.remove(2)<br>>>> set1<br>{1, 3}<br>>>> set1.remove(4)<br>报错|
|symmetric_difference()	|set3 = set1.symmetric_difference(set2)|	取 set1 和 set2 中互不相同的元素，给 set3	| >>> set1 = {1,2,3}<br>>>> set2 = {3,4}<br>>>> set3 = set1.symmetric_difference(set2)<br>>>> set3<br>{1, 2, 4}|
|symmetric_difference_update()	|set1.symmetric_difference_update(set2)|	取 set1 和 set2 中互不相同的元素，并更新给 set1|	>>> set1 = {1,2,3}<br>>>> set2 = {3,4}<br>>>> set1.symmetric_difference_update(set2)<br>>>> set1<br>{1, 2, 4}|
|union()|	set3 = set1.union(set2)	|取 set1 和 set2 的并集，赋给 set3|	>>> set1 = {1,2,3}<br>>>> set2 ={3,4}<br>>>> set3=set1.union(set2)<br>>>> set3<br>{1, 2, 3, 4}|
|update()|	set1.update(elem)	|添加列表或集合中的元素到 set1|	>>> set1 = {1,2,3}<br>>>> set1.update([3,4])<br>>>> set1<br>{1,2,3,4}|

表 1 Python set方法