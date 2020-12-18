前面使用 print() 函数时，都只输出了一个变量，但实际上 print() 函数完全可以同时输出多个变量，而且它具有更多丰富的功能。

print() 函数的详细语法格式如下：
```python
print (value,...,sep='',end='\n',file=sys.stdout,flush=False)
```

从上面的语法格式可以看出，value 参数可以接受任意多个变量或值，因此 print() 函数完全可以输出多个值。例如如下代码：
```python
user_name ＝ 'Charlie'
user_age = 8
#同时输出多个变量和字符串
print("读者名：",user_name,"年龄：",user_age)
```
运行上面代码，可以看到如下输出结果：
```consle
读者名： Charlie 年龄： 8
```

从输出结果来看，使用 print() 函数输出多个变量时，print() 函数默认以空格隔开多个变量，如果读者希望改变默认的分隔符，可通过 sep 参数进行设置。例如输出语句：
```python
#同时输出多个变量和字符串，指定分隔符
print("读者名：" ,user_name,"年龄：",user_age,sep='|')
```

运行上面代码，可以看到如下输出结果：
```consle
读者名：|Charlie|年龄：|8
```


在默认情况下，print() 函数输出之后总会换行，这是因为 print() 函数的 end 参数的默认值是“\n”，这个“\n”就代表了换行。如果希望 print() 函数输出之后不会换行，则重设 end 参数即可，例如如下代码：
```python
#设置end 参数，指定输出之后不再换行
print(40,'\t',end＝"")
print(5O,'\t',end＝"")
print(60,'\t',end＝"")
```
上面三条 print() 语句会执行三次输出，但由于它们都指定了 end＝""，因此每条 print() 语句的输出都不会换行，依然位于同一行。运行上面代码，可以看到如下输出结果：
```consle
40    50    60
```

file 参数指定 print() 函数的输出目标，file 参数的默认值为 sys.stdout，该默认值代表了系统标准输出，也就是屏幕，因此 print() 函数默认输出到屏幕。实际上，完全可以通过改变该参数让 print() 函数输出到特定文件中，例如如下代码：
```python
f = open("demo.txt","w")#打开文件以便写入
print('沧海月明珠有泪',file=f)
print('蓝回日暖玉生烟',file=f)
f.close()
```|
上面程序中，open() 函数用于打开 demo.txt 文件，接连 2 个 print 函数会将这 2 段字符串依次写入此文件，最后调用 close() 函数关闭文件，教程后续章节还会详细介绍关于文件操作的内容。

print() 函数的 flush 参数用于控制输出缓存，该参数一般保持为 False 即可，这样可以获得较好的性能。