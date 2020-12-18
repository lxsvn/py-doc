input() 是 Python 的内置函数，用于从控制台读取用户输入的内容。input() 函数总是以字符串的形式来处理用户输入的内容，所以用户输入的内容可以包含任何字符。

input() 函数的用法为：
```python
str = input(tipmsg)
```
说明：
- str 表示一个字符串类型的变量，input 会将读取到的字符串放入 str 中。
- tipmsg 表示提示信息，它会显示在控制台上，告诉用户应该输入什么样的内容；如果不写 tipmsg，就不会有任何提示信息。

【实例】input() 函数的简单使用：
```python
a = input("Enter a number: ")
b = input("Enter another number: ")
print("aType: ", type(a))
print("bType: ", type(b))
result = a + b
print("resultValue: ", result)
print("resultType: ", type(result))
```
运行结果示例：
```consle
Enter a number: 100↙
Enter another number: 45↙
aType:  <class 'str'>
bType:  <class 'str'>
resultValue:  10045
resultType:  <class 'str'>
```
↙表示按下回车键，按下回车键后 input() 读取就结束了。

本例中我们输入了两个整数，希望计算出它们的和，但是事与愿违，Python 只是它们当成了字符串，+起到了拼接字符串的作用，而不是求和的作用。

我们可以使用 Python 内置函数将字符串转换成想要的类型，比如：
- int(string) 将字符串转换成 int 类型；
- float(string) 将字符串转换成 float 类型；
- bool(string) 将字符串转换成 bool 类型。

修改上面的代码，将用户输入的内容转换成数字：

```python
a = input("Enter a number: ")
b = input("Enter another number: ")
a = float(a)
b = int(b)
print("aType: ", type(a))
print("bType: ", type(b))
result = a + b
print("resultValue: ", result)
print("resultType: ", type(result))
```

运行结果：
```consle
Enter a number: 12.5↙
Enter another number: 64↙
aType:  <class 'float'>
bType:  <class 'int'>
resultValue:  76.5
resultType:  <class 'float'>
```