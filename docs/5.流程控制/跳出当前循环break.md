我们知道，在执行 while 循环或者 for 循环时，只要循环条件满足，程序将会一直执行循环体，不停地转圈。但在某些场景，我们可能希望在循环结束前就强制结束循环，Python 提供了 2 种强制离开当前循环体的办法：
- 使用 continue 语句，可以跳过执行本次循环体中剩余的代码，转而执行下一次的循环。
- 只用 break 语句，可以完全终止当前循环。

本节先讲解 break 的用法，continue 语句放到下节做详细介绍。

break 语句可以立即终止当前循环的执行，跳出当前所在的循环结构。无论是 while 循环还是 for 循环，只要执行 break 语句，就会直接结束当前正在执行的循环体。

这就好比在操场上跑步，原计划跑 10 圈，可是当跑到第 2 圈的时候，突然想起有急事要办，于是果断停止跑步并离开操场，这就相当于使用了 break 语句提前终止了循环。

break 语句的语法非常简单，只需要在相应 while 或 for 语句中直接加入即可。例如如下程序：
```python
add = "https://doc-py.she-tech.cn/#/"
# 一个简单的for循环
for i in add:
    if i == ',' :
        #终止循环
        break
    print(i,end="")
print("\n执行循环体外的代码")
```
运行结果为：
```consle
https://doc-py.she-tech.cn/#/
执行循环体外的代码
```

分析上面程序不难看出，当循环至 add 字符串中的逗号（ , ）时，程序执行 break 语句，其会直接终止当前的循环，跳出循环体。
break 语句一般会结合 if 语句进行搭配使用，表示在某种条件下跳出循环体。

注意，通过前面的学习我们知道，for 循环后也可以配备一个 else 语句。这种情况下，如果使用 break 语句跳出循环体，不会执行 else 中包含的代码。举个例子：
```python
add = "https://doc-py.she-tech.cn/#/"
for i in add:
    if i == ',' :
        #终止循环
        break
    print(i,end="")
else:
    print("执行 else 语句中的代码")
print("\n执行循环体外的代码")
```

程序执行结果为：
```consle
https://doc-py.she-tech.cn/#/
执行循环体外的代码
```
从输出结果可以看出，使用 break 跳出当前循环体之后，该循环后的 else 代码块也不会被执行。但是，如果将 else 代码块中的代码直接放在循环体的后面，则该部分代码将会被执行。

另外，对于嵌套的循环结构来说，break 语句只会终止所在循环体的执行，而不会作用于所有的循环体。举个例子：
```python
add = "https://doc-py.she-tech.cn/#/"
for i in range(3):
    for j in add:
        if j == ',':
            break   
        print(j,end="")
    print("\n跳出内循环")
```
程序执行结果为：
```consle
https://doc-py.she-tech.cn/#/
跳出内循环
https://doc-py.she-tech.cn/#/
跳出内循环
https://doc-py.she-tech.cn/#/
跳出内循环
```

分析上面程序，每当执行内层循环时，只要循环至 add 字符串中的逗号（ , ）就会执行 break 语句，它会立即停止执行当前所在的内存循环体，转而继续执行外层循环。

那么在嵌套循环结构中，如何同时跳出内层循环和外层循环呢？最简单的方法就是借用一个 bool 类型的变量。

修改上面的程序：
```python
add = "https://doc-py.she-tech.cn/#/"
#提前定义一个 bool 变量，并为其赋初值
flag = False
for i in range(3):
    for j in add:
        if j == ',':
            #在 break 前，修改 flag 的值
            flag = True
            break   
        print(j,end="")
    print("\n跳出内循环")
    #在外层循环体中再次使用 break
    if flag == True:
        print("跳出外层循环")
        break
```
可以看到，通过借助一个 bool 类型的变量 flag，在跳出内循环时更改 flag 的值，同时在外层循环体中，判断 flag 的值是否发生改动，如有改动，则再次执行 break 跳出外层循环；反之，则继续执行外层循环。

因此，上面程序的执行结果为：
```consle
https://doc-py.she-tech.cn/#/
跳出内循环
跳出外层循环
```
当然，这里仅跳出了 2 层嵌套循环，此方法支持跳出多层嵌套循环。