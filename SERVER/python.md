# python 入门

## 数据类型和变量

### 字符串

转义字符\可以转义很多字符，比如`\n`表示换行，`\t`表示制表符

Python允许用'''...'''的格式表示多行内容

### 布尔值

一个布尔值只有`True`、`False`两种值

布尔值可以用`and`、`or`和`not`运算。 `and`运算是与运算; `or`运算是或运算; `not`运算是非运算

### 变量

变量本身类型不固定的语言称之为动态语言，与之对应的是静态语言。

静态语言在定义变量时必须指定变量类型，如果赋值的时候类型不匹配，就会报错。

### 常量

在Python中，通常用全部大写的变量名表示常量

### Python的字符串

因为Python的诞生比Unicode标准发布的时间还要早，所以最早的Python只支持ASCII编码，

普通的字符串'ABC'在Python内部都是ASCII编码的。Python提供了`ord()`和`chr(`函数，可以把字母和对应的数字相互转换

Python在后来添加了对Unicode的支持，以Unicode表示的字符串用`u'...'`表示

在Python 3.x版本中，把'xxx'和u'xxx'统一成Unicode编码，即写不写前缀u都是一样的，而以字节形式表示的字符串则必须加上b前缀：b'xxx'。

### 格式化

在Python中，采用的格式化方式和C语言是一致的，用`%`实现，举例如下：

```python
>>> 'Hello, %s' % 'world'
'Hello, world'
>>> 'Hi, %s, you have $%d.' % ('Michael', 1000000)
'Hi, Michael, you have $1000000.'
```

常见的占位符

* `%d`: 整数

* `%f`: 浮点数

* `%s`: 字符串

* `%x`: 十六进制整数

## list和tuple

### list

Python内置的一种数据类型是列表：list。list是一种有序的集合，可以随时添加和删除其中的元素。

```python
>>> classmates = ['Michael', 'Bob', 'Tracy']
>>> classmates
['Michael', 'Bob', 'Tracy']
```

变量classmates就是一个list。用`len()`函数可以获得list元素的个数

* list是一个可变的有序表，所以，可以往list中追加元素到末尾：

```python
>>> classmates.append('Adam')
>>> classmates
['Michael', 'Bob', 'Tracy', 'Adam']
```

* 也可以把元素插入到指定的位置，比如索引号为1的位置：

```python
>>> classmates.insert(1, 'Jack')
>>> classmates
['Michael', 'Jack', 'Bob', 'Tracy', 'Adam']
```

* 要删除list末尾的元素，用`pop()`方法：

```python
>>> classmates.pop()
'Adam'
>>> classmates
['Michael', 'Jack', 'Bob', 'Tracy']
```

* 要删除指定位置的元素，用`pop(i)`方法，其中i是索引位置：

```python
>>> classmates.pop(1)
'Jack'
>>> classmates
['Michael', 'Bob', 'Tracy']
```

* 要把某个元素替换成别的元素，可以直接赋值给对应的索引位置：

```python
>>> classmates[1] = 'Sarah'
>>> classmates
['Michael', 'Sarah', 'Tracy']
```

* list里面的元素的数据类型也可以不同

* list元素也可以是另一个list

### tuple

另一种有序列表叫元组：tuple。tuple和list非常类似，但是tuple一旦初始化就不能修改

## 条件判断和循环

### 条件判断

```python
if <条件判断1>:
    <执行1>
elif <条件判断2>:
    <执行2>
elif <条件判断3>:
    <执行3>
else:
    <执行4>
```
注意不要少写了冒号:

### 循环

Python的循环有两种，一种是`for...in`循环，

```python
names = ['Michael', 'Bob', 'Tracy']
for name in names:
    print name
    
res:
Michael
Bob
Tracy
```

所以for x in ...循环就是把每个元素代入变量x，然后执行缩进块的语句。

`range()`函数，可以生成一个整数序列，比如`range(5)`生成的序列是从0开始小于5的整数

第二种循环是`while`循环，只要条件满足，就不断循环，条件不满足时退出循环。

```python
while <条件判断1>：
  <执行1>
```

## dict和set

### dict

如果key不存在，dict就会报错：

```python
>>> d['Thomas']
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'Thomas'
```

要避免key不存在的错误，有两种办法，一是通过`in`判断key是否存在

二是通过dict提供的get方法，如果key不存在，可以返回None，或者自己指定的value：

```python
>>> d.get('Thomas')
>>> d.get('Thomas', -1)
-1
```

