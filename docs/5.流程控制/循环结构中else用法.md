Python 中，无论是 while 循环还是 for 循环，其后都可以紧跟着一个 else 代码块，它的作用是当循环条件为 False 跳出循环时，程序会最先执行 else 代码块中的代码。

以 while 循环为例，下面程序演示了如何为 while 循环添加一个 else 代码块：
```python
add = "https://doc-py.she-tech.cn/"
i = 0
while i < len(add):
    print(add[i],end="")
    i = i + 1
else:
    print("\n执行 else 代码块")
```
程序执行结果为：
```consle
https://doc-py.she-tech.cn/
执行 else 代码块
```

上面程序中，当i==len(add)结束循环时（确切的说，是在结束循环之前），Python 解释器会执行 while 循环后的 else 代码块。

有读者可能会觉得，else 代码块并没有什么具体作用，因为 while 循环之后的代码，即便不位于 else 代码块中，也会被执行。例如，修改上面程序，去掉 else 代码块：
```python
add = "https://doc-py.she-tech.cn/"
i = 0
while i < len(add):
    print(add[i],end="")
    i = i + 1
#原本位于 else 代码块中的代码
print("\n执行 else 代码块")
```
程序执行结果为：
```consle
https://doc-py.she-tech.cn/
执行 else 代码块
```

那么，else 代码块真的没有用吗？当然不是。后续章节介绍 break 语句时，会具体介绍 else 代码块的用法。

当然，我们也可以为 for 循环添加一个 else 代码块，例如：
```python
add = "https://doc-py.she-tech.cn/"
for i in  add:
    print(i,end="")
else:
    print("\n执行 else 代码块")
```
程序执行结果为：
```consle
https://doc-py.she-tech.cn/
执行 else 代码块
```