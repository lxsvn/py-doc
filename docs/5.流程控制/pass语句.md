在实际开发中，有时候我们会先搭建起程序的整体逻辑结构，但是暂时不去实现某些细节，而是在这些地方加一些注释，方面以后再添加代码，请看下面的例子：
```python
age = int( input("请输入你的年龄：") )
if age < 12 :
    print("婴幼儿")
elif age >= 12 and age < 18:
    print("青少年")
elif age >= 18 and age < 30:
    print("成年人")
elif age >= 30 and age < 50:
    # 暂定
else:
    print("老年人")
```

当年龄大于等于 30 并且小于 50 时，我们没有使用 print() 语句，而是使用了一个注释，希望以后再处理成年人的情况。当 Python 执行到该 elif 分支时，会跳过注释，什么都不执行。

但是 Python 提供了一种更加专业的做法，就是空语句 pass。pass 是 Python 中的关键字，用来让解释器跳过此处，什么都不做。

就像上面的情况，有时候程序需要占一个位置，或者放一条语句，但又不希望这条语句做任何事情，此时就可以通过 pass 语句来实现。使用 pass 语句比使用注释更加优雅。

使用 pass 语句更改上面的代码：
```python
age = int( input("请输入你的年龄：") )
if age < 12 :
    print("婴幼儿")
elif age >= 12 and age < 18:
    print("青少年")
elif age >= 18 and age < 30:
    print("成年人")
elif age >= 30 and age < 50:
    pass
else:
    print("老年人")
```
运行结果：
```consle
请输入你的年龄：40↙
```

从运行结果可以看出，程序虽然执行到第 30~50年龄的判断，但是并没有进行什么操作。