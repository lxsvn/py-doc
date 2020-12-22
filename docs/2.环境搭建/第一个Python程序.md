Python 使用 print 函数在屏幕上输出一段文本，输出结束后会自动换行。
## 在屏幕上输出字符串
字符串就是多个字符的集合，由双引号" "或者单引号' '包围，例如：
```consle
"Hello World"
"Number is 198"
'Pyhon：http://doc-py.she-tech.cn/'
```

字符串中可以包含英文、数字、中文以及各种符号。

print 输出字符串的格式如下：
```python
print("字符串内容")
```

或者
```python
print('字符串内容')
```

字符串要放在小括号( )中传递给 print，让 print 把字符串显示到屏幕上，这种写法在 Python 中被称为函数（Function）。

需要注意的是，引号和小括号都必须在英文半角状态下输入，而且 print 的所有字符都是小写。Python 是严格区分大小写的，print 和 Print 代表不同的含义。

print 用法举例：
```python
print("Hello World!")  #输出英文
print("Number is 198")  #输出数字
print("Pyhon：http://doc-py.she-tech.cn/")  #输出中文
``` 

也可以将多段文本放在一个 print 函数中：
```python
print(
    "Hello World!"
    "Number is 198"
    "http://doc-py.she-tech.cn/"
);
print("Hello World!" "Python is great!" "Number is 198.")
print(
    "Hello World!\n"
    "Number is 198\n"
    "http://doc-py.she-tech.cn/"
);
```
注意，同一个 print 函数的字符串之间不会自动换行，加上\n才能看到换行效果。

将多个字符串放在一个print中 
## 对分号的说明
有编程经验的读者应该知道，很多编程语言（比如C语言、C++、Java 等）都要求在语句的最后加上分号;，用来表示一个语句的结束。但是 Python 比较灵活，它不要求语句使用分号结尾；当然也可以使用分号，但并没有实质的作用（除非同一行有更多的代码），而且这种做法也不是 Python 推荐的。

修改上面的代码，加上分号：
```python
print(198);
print("Hello World!"); print("Python is good!");
print("Pyhon：http://doc-py.she-tech.cn/");
```
运行结果：
```consle
198
Hello World!
Python is good!
Pyhon：http://doc-py.she-tech.cn/
```

注意第 2 行代码，我们将两个 print 语句放在同一行，此时必须在第一个 print 语句最后加分号，否则会导致语法错误。
## 对 Python 2.x 的说明
Python 3.x 要求在使用函数时加上小括号( )，但是以前的 Python 2.x 版本可以省略小括号，也即是写成下面的样子：
```python
print 198
print "Hello World!";  #末尾也可以加上分号
print "Pyhon：http://doc-py.she-tech.cn/"
```
我建议大家加上小括号，这样写比较容易理解，而且兼容性好。
**在屏幕上输出数字**
print 除了能输出字符串，还能输出数字，将数字或者数学表达式直接放在 print 中就可以输出，如下所示：
```python
print( 100 )
print( 65 )
print( 100 + 12 )
print( 8 * (4 + 6) )
```

注意，输出数字时不能用引号包围，否则就变成了字符串。下面的写法就是一个反面教材，数学表达式会原样输出：
```python
print("100 + 12")
```

运行结果是100 + 12，而不是 112。

另外，和输出字符串不同，不能将多个数字放在一个 print 函数中。例如，下面的写法就是错误的：
```python
print( 100 12 95 );
print(
    80
    26
    205
);
```
总结
> Python 程序的写法比较简单，直接书写功能代码即可，不用给它套上“外壳”。下面我们分别使用C语言、Java 和 Python 输出，让大家对比感受一下。

使用C语言：
```C
#include <stdio.h>
int main()
{
    puts("Pyhon：http://doc-py.she-tech.cn/");
    return 0;
}
``` 
使用 Java：
```java
public class HelloJava {
    public static void main(String[] args) {
        System.out.println("Pyhon：http://doc-py.she-tech.cn/");
    }
}
```

使用 Python：
```python
print("Pyhon：http://doc-py.she-tech.cn/")
```