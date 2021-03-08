
<center><h1>使用python写入excel数据<h1></center>

## 一：使用python写入excel数据

**使用 第三方库 openpyxl 写入 excel数据：**
```python

# 导入第三方库(插件)
import openpyxl

# 1. 定义excel操作对象
wb = openpyxl.Workbook()

# 2. 激活 excel工作簿
ws = wb.active

# 3. 添加表头
ws.append(['日期', '订单号', '总价'])

# 4. 添加行数据
ws.append(['2020-10-01','N01920192',991])
ws.append(['2020-10-02','N01920193',50])
ws.append(['2020-10-03','N01920194',102])
ws.append(['2020-10-04','N01920195',78])

# 5. 保存更改（指定绝对路径：保存的文件名和地址）
wb.save('excels/t1.xlsx')

```


## openpyxl：操作excel的第三方库
```
官方文档：https://openpyxl.readthedocs.io/en/stable/
```

##  openpyxl：常用配置

```python

# 设置指定列的的宽度

ws.column_dimensions['A'].width = 20.0
ws.column_dimensions['B'].width = 20.0
ws.column_dimensions['C'].width = 35.0
ws.column_dimensions['D'].width = 10.0
ws.column_dimensions['E'].width = 10.0


```