和 break 语句相比，continue 语句的作用则没有那么强大，它只会终止执行本次循环中剩下的代码，直接从下一次循环继续执行。

> 仍然以在操作跑步为例，原计划跑 10 圈，但当跑到 2 圈半的时候突然接到一个电话，此时停止了跑步，当挂断电话后，并没有继续跑剩下的半圈，而是直接从第 3 圈开始跑。

continue 语句的用法和 break 语句一样，只要 while 或 for 语句中的相应位置加入即可。例如：
```python
add = "http://doc-py.she-tech.cn/"
# 一个简单的for循环
for i in add:
    if i == ',' :
        # 忽略本次循环的剩下语句
        print('\n')
        continue
    print(i,end="")
```    
运行上面程序，将看到如下运行结果：
```consle
http://doc-py.she-tech.cn/
http://doc-py.she-tech.cn/
```

可以看到，当遍历 add 字符串至逗号（ , ）时，会进入 if 判断语句执行 print() 语句和 continue 语句。其中，print() 语句起到换行的作用，而 continue 语句会使 Python 解释器忽略执行第 8 行代码，直接从下一次循环开始执行。
