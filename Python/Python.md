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


<!--
 * @Date: 2019-08-23 15:33:45
 * @LastEditors: LuneShao
 * @LastEditTime: 2019-09-17 14:25:33
 -->

-------

以下内容来源于廖雪峰教程的笔记
于20191129更新

-------

## if 语句

- 以#开头的语句是注释，注释是给人看的，可以是任意内容，解释器会忽略掉注释。
- 其他每一行都是一个语句，当语句以冒号:结尾时，缩进的语句视为代码块。
- 按照约定俗成的管理，应该始终坚持使用 **4** 个空格的缩进。

## 数据类型

- Python 还允许用 r''表示''内部的字符串默认不转义。
- 空值是 Python 里一个特殊的值，用 None 表示。
- Python 允许用'''...'''的格式表示多行内容。
- 在 Python 中，通常用全部大写的变量名表示常量

## 字符集

ascii => unicode => utf-8

```py
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
```

第一行注释是为了告诉 Linux/OS X 系统，这是一个 Python 可执行程序，Windows 系统会忽略这个注释；
第二行注释是为了告诉 Python 解释器，按照 UTF-8 编码读取源代码，否则，你在源代码中写的中文输出可能会有乱码。

### 格式化

```
print('hello, %.2f' % ((85 - 72) / 85))
print('hello, {0:.2f}'.format(((85 - 72) / 85)))
```

## list&tuple

- append()
- insert(index, item) 添加元素
- pop(index) 删除元素
- 当索引超出了范围时，Python 会报一个 IndexError 错误

tuple 另一种有序列表叫元组,一旦初始化就不能修改

- 只有 1 个元素的 tuple 定义时必须加一个逗号 t = (1,)

## 循环 for & while

- break & continue 停止循环，continue 语句会直接继续下一轮循环，后续的语句不会执行

## 字典

1. 要避免 key 不存在的错误，有两种办法：
   - 一是通过 in 判断 key 是否存在
   - 二是通过 dict 提供的 get('key', custom return value) 方法，如果 key 不存在，可以返回 None，或者自己指定的 value。
2. 要删除一个 key，用 pop(key)方法
3. set 的原理和 dict 一样，所以，同样不可以放入可变对象，因为无法判断两个可变对象是否相等，也就无法保证 set 内部“不会有重复元素”。

## 函数

1. 定义函数 `def 关键字 + 函数名 + ( 参数 ):`
2. 如果没有 return 语句，函数执行完毕后也会返回结果，只是结果为 None
3. 用`from abstest import my_abs`来导入 my_abs()函数
4. 定义一个空函数可以用 `pass`
5. 数据类型检查可以用内置函数`isinstance()`
6. 定义默认参数要牢记一点：默认参数必须指向不变对象！`def func (name, gender, age=6, city='beijing')`
7. 可变参数 `def func (*args):`，如果有一个 list 或 tuple，可以 `func(*list)`这样传递

### 参数类型

1. 位置参数，固定参数数量
2. 可变参数 `def func (*args):`，可以传入不定数量的参数
3. 关键字参数 `def func (**kw):`，传入的参数被组成一个`dict`，也可以确定接受参数的 key 值，`def func(*, name, gender)`

## 高级特性

1. list 索引：enumerate(list)
2. 遍历字典值 d.values()， 键值对 dict.items()
3. 通过 collections 模块的 Iterable 类型判断对象是可迭代对象

```py
>>> from collections import Iterable
>>> isinstance('abc', Iterable) # str是否可迭代
True
>>> isinstance([1,2,3], Iterable) # list是否可迭代
True
>>> isinstance(123, Iterable) # 整数是否可迭代
False
```

## 高阶函数

1. 一个函数就可以接收另一个函数作为参数，这种函数就称之为高阶函数。
2. sorted()函数也是一个高阶函数，它还可以接收一个 key 函数来实现自定义的排序
3. 高阶函数除了可以接受函数作为参数外，还可以把函数作为结果值返回。
4. 嵌套函数引用外部变量的方法 `nonlocal var`
5. 匿名函数：lamba x: x \* x，lamba(关键字) 参数 : 表达式
6. 在代码运行期间动态增加功能的方式，称之为“装饰器”（Decorator）。
7. functools.wraps，把原始函数的**name**等属性复制到装饰器函数中

## 模块

1. 每一个包目录下面都会有一个**init**.py 的文件，这个文件是必须存在的，否则，Python 就把这个目录当成普通目录，而不是一个包。
2. 通过 `_` 前缀来实现公有私有变量、函数

## 面向对象

1. 定义类是通过`class`关键字

```py
class Student(object): # class Student(类名) (object: 表示该类是从哪个类继承下来的)
    pass
```

2. 注意到`__init__`方法的第一个参数永远是`self`，表示创建的实例本身，
3. 如果要让内部属性不被外部访问，可以把属性的名称前加上两个下划线\_\_
4. 和普通的函数相比，在类中定义的函数只有一点不同，就是第一个参数永远是实例变量`self`，并且，调用时，不用传递该参数
5. 封装：对象定义属性和内部定义访问数据的函数
6. 继承：`class Dog(Animal):`子类获得了父类的全部功能，子类覆盖了父类的同名方法
7. 多态：允许新增 Animal 子类；不需要修改依赖 Animal 类型的 run_twice()等函数。

### 高级编程

1. 定义一个特殊的**slots**变量，来限制该 class 实例能添加的属性

```py
class Student(object):
    __slots__ = ('name', 'age') # 用tuple定义允许绑定的属性名称
```

2. **slots**定义的属性仅对当前类实例起作用，对继承的子类是不起作用的
3. 实现自定义的实例输出，使用 `__str__()` 返回一个自定义字符串
4. 如果一个类想实现迭代，就必须实现一个`__iter__()`方法，方法返回一个可迭代对象。Python 的 for 循环就会不断调用该迭代对象的**next**()方法拿到循环的下一个值，直到遇到 StopIteration 错误时退出循环。
5. `__getitem__`实现对象的类数组索引取值
6. `__getattr__()`预处理对象没有的属性
7. 枚举类：

```py
# 1 默认分配 value, int类型，从1开始
Month = Enum('month', ('Sat', 'Feb', ..., 'Dec'))
# 2
from enum import Enum, unqiue

@unqiue # 确保键的唯一性
class Month (Enum):
    Jan = 1
    Feb = 2
    ...
    Dec = 12
```

8. type 创建类：

```py
def fn(self, name):
    print('hello %s' % name)

Hello = type('Hello', (object, ), dict(hello=fn))
```

参数分别为：

- 第一个参数：类名
- 第二个参数：继承的类
- 第三个参数：方法名称与函数绑定

## 错误

1. raise 语句如果不带参数，就会把当前错误原样抛出。
2. 调试错误：断言 如果 assert 后的条件为 false 则程序错误，会抛错。
3. 输出是否是我们所期望的。最常用的断言就是 assertEqual()
4. 另一种重要的断言就是期待抛出指定类型的 Error，比如通过 d['empty']访问不存在的 key 时，断言会抛出 KeyError

```py
with self.assertRaises(KeyError):
    value = d['empty']
```

5. 单元测试的测试用例要覆盖常用的输入组合、边界条件和异常。
   运行方式

- 最后加上两行代码：

```py
if __name__ == '__main__':
    unittest.main()
```

- 另一种方法是在命令行通过参数-m unittest 直接运行单元测试

- 可以在单元测试中编写两个特殊的`setUp()`和`tearDown()`方法。这两个方法会分别在每调用一个测试方法的前后分别被执行。

## IO 操作

1. Python 引入了 with 语句来自动帮我们调用 close()方法：

```py
# 不必调用f.close()方法
with open('/path/to/file', 'r') as f:
    print(f.read())
```

2. 像 open()函数返回的这种有个 read()方法的对象，在 Python 中统称为 file-like Object。

3. 要读取二进制文件，比如图片、视频等等，用'rb'模式打开文件即可：

```py
>>> f = open('/Users/michael/test.jpg', 'rb')
>>> f.read()
```

4. 以'w'模式写入文件时，如果文件已存在，会直接覆盖（相当于删掉后新写入一个文件）。如果我们希望追加到文件末尾可以传入'a'以追加（append）模式写入。

```py
with open('/Users/apple/Documents/usrTest/python/0830/io/test.txt', 'ab') as f:

    f.write('heiheiheiheiheiheiheihei你好'.encode('utf-8'))
```

### 操作文件目录 os 模块

1. os.name、os.uname() 获取系统的名字和详细信息
2. os.environ 获取环境变量，要获取某个环境变量的值，可以调用 os.environ.get('key')

3. 我们把变量从内存中变成可存储或传输的过程称之为序列化

### 序列化

1. pickle：pickle.dumps() 序列化，pickle.dump() 转化为 file-like obj，pickle.load() 反序列化

2. json 同

```py
import json
sdict = '{a: 10}'
# json.loads() 解析为dict
fdict = json.loads(sdict)
# json.dumps() 解析为字符串
sdict = json.dumps(fidct)
# json.load() 读取文件
with open('path', 'r') as file:
    f = json.load(file) # 参数 fp类型
# json.dump() 写入文件
with open('path', 'w') as file:
    json.dump(sdict, file)
```

## 进程&线程

1. os.fork() 和 Process() 的方式创建子进程。os.getppid():父进程的 id，os.getpid()子进程的 id

```py
# os.fork()
pid = os.fork()
# from multiprocessing import Process
def run_proc(name):
    print('its child process %s(%s)' % (name, os.getpid()))


p = Process(target=run_proc, args=('test',))
p.start()
p.join() # join()方法可以等待子进程结束后再继续往下运行
```

2. subprocess 模块可以让我们非常方便地启动一个子进程，然后控制其输入和输出。
3. threading.Tread(target=func, args=('', ), name='name') 创建线程
4. threading.Lock() 为线程创建一个锁，避免干扰，lock.acquire() 、 lock.release() 获取和释放。不释放

## 常用内建模块

### datetime

1. timestamp 的值与时区毫无关系,当前时间就是相对于 epoch time(utc=0)的秒数，称为 timestamp。
2. 时区转换：我们可以先通过 utcnow()拿到当前的 UTC 时间，再转换为任意时区的时间

### base64

1. base64.b64encode()、base64.b64encode()：二进制编码、解码
2. base64.urlsafe_b64encode()、base64.urlsafe_b64decode()：URL 中编码

如果要编码的二进制数据不是 3 的倍数，最后会剩下 1 个或 2 个字节怎么办？Base64 用\x00 字节在末尾补足后，再在编码的末尾加上 1 个或 2 个=号，表示补了多少字节，解码的时候，会自动去掉。

### collections

- namedtuple：命名 tuple，可以根据属性来引用。

```py
>>> from collections import namedtuple
>>> Point = namedtuple('Point', ['x', 'y'])
>>> p = Point(1, 2)
>>> p.x
1
>>> p.y
2
```

- deque：为了高效实现插入和删除操作的双向列表，适合用于队列和栈

```py
>>> from collections import deque
>>> q = deque(['a', 'b', 'c'])
>>> q.append('x')
>>> q.appendleft('y')
>>> q
deque(['y', 'a', 'b', 'c', 'x'])
```

- defaultdict：key 不存在时，返回一个默认值

```py
from collections import defaultdict
defdic = defaultdict(lamda: 'N/A')
defdic['a'] = 'a'
print(defdic['b'])
> 'N/A'
```

- OrderedDict：使用 dict 时，保持 Key 的顺序

```py
dic = OrderedDict([('a': 1, 'b': 2, 'c': 3)])
```

- Counter：计数器

```py
from collections import Counter
c = Counter()
for ch in 'programmings':
    c[ch] = c[ch] + 1

c
>Counter({'g': 2, 'm': 2, 'r': 2, 'a': 1, 'i': 1, 'o': 1, 'n': 1, 'p': 1})
```

### struct

`bytes`和其他二进制数据类型的转换

```py
struct.pack('>I', 10240099)
> b'\x00\x9c@c'
```

pack 的第一个参数是处理指令，'>I'的意思是,`>`表示字节顺序是 [big-endian](https://blog.csdn.net/sunshine1314/article/details/2309655)(大端字节序，高位有效字节存储在低位)，也就是网络序，`I` 表示 4 字节无符号整数，`H`：2 字节无符号整数。
后面的参数个数要和处理指令一致。

```py
struct.unpack('>IH', b'\xf0\xf0\xf0\xf0\x80\x80')
```

### hashlib

摘要算法又称哈希算法、散列算法。它通过一个函数，把任意长度的数据转换为一个长度固定的数据串

- md5：32 位的 16 进制。对简单口令加强保护：对原始口令加一个复杂字符串来实现，俗称“加盐”。
- sha：sha1(40 位 16 进制)、sha256、sha512

```py
import hashlib
md5 = hashlib.md5()
md5.update('str need to encode' + 'the salt'.encode('ascii'))
print(md5.hexdigest())
```

### hmac

在计算哈希的过程中，把 key 混入计算过程中。

```py
import hmac
msg = b'hello'
key = 'secret'.encode('utf-8')
h = hmac.new(key, msg, digestmod='MD5')
print(h.hexdigest())
```

## itertools

- itertools.count()：创建一个无限迭代器，for 循环可取出自然数序列
- itertools.cycle('str')：会把传入的一个序列无限重复下去
- itertools.repeat('str', count)：负责把一个元素无限重复下去，不过如果提供第二个参数就可以限定重复次数
- itertools.chain()：可以把一组迭代对象串联起来，形成一个更大的迭代器
- itertools.groupby()：把迭代器中相邻的重复元素挑出来放在一起

通过 takewhile()等函数根据条件判断来截取出一个有限的序列

## contextlib

- @contextmanager：@contextmanager 这个 decorator 接受一个 generator，用 yield 语句把 with ... as var 把变量输出出去

```py
from contextlib import contextmanager
class Query(object):
    def __init__(self, name):
        self.name = name
    def query(self):
        print('hello %s' % self.name)

@contextmanager
def create_query(name):
    q = Query(name)
    yield q

with create_query(name) as qu:
    ...
```

- @closing：这个对象就是一个上下文管理器，它的**exit**函数仅仅调用传入参数的 close 函数

````py
# closing 源码如下：
class closing(object):
    def __init__(self, thing):
        self.thing = thing
    def __enter__(self):
        return self.thing
    def __exit__(self, *exc_info):
        self.thing.close()
```//anaconda3/envs/python37/lib/python3.7/site-packages


> 所以 closeing 上下文管理器仅使用于具有 close()方法的资源对象。

## with 语句

[with 语句上下文管理器](https://www.cnblogs.com/nnnkkk/p/4309275.html)

一个类只要实现了 `__enter__()` 和 `__exit__()`，我们就称之为上下文管理器。如果我们要自定义一个上下文管理器，只需要定义一个类并且是实现 `__enter__()` 和 `__exit__()` 即可。

`__enter__()`：主要执行一些环境准备工作，同时返回一资源对象。
`__exit()__()`：完整形式为 `__exit__(type, value, traceback)`,这三个参数和调用 `sys.exec_info()` 函数返回值是一样的，分别为异常类型、异常信息和堆栈。

## urllib

- request 模块：抓取 URL 内容，也就是发送一个 GET 请求到指定的页面，然后返回 HTTP 的响应。如果我们要想模拟浏览器发送 GET 请求，就需要使用 Request 对象，通过往 Request 对象添加 HTTP 头，我们就可以把请求伪装成浏览器。

```py
from urllib import request
with request.urlopen('/path') as file:
    data = file.read()
    print(data.decode('utf-8'))
````

### HTMLParse

解析 HTML

- HTMLParser.feed(data)：填充一些文本到解析器中。如果包含完整的元素，则被处理；如果数据不完整，将被缓冲直到更多的数据被填充，或者 close() 被调用。data 必须为 str 类型。

- HTMLParser.close()：如同后面跟着一个文件结束标记一样，强制处理所有缓冲数据。

- HTMLParser.reset()：重置实例。丢失所有未处理的数据。在实例化阶段被隐式调用。

- HTMLParser.getpos()：返回当前行号和偏移值。

- HTMLParser.get_starttag_text()：返回最近打开的开始标记中的文本。

- HTMLParser.handle_starttag(tag, attrs)：在标签开始的时候被调用，tag 参数是小写的标记名。attrs 参数是一个 (name, value) 形式的列表。

- HTMLParser.handle_endtag(tag)：处理元素的结束标记

- HTMLParser.handle_startendtag(tag, attrs)：在解析器遇到 XHTML 样式的空标记时被调用（ <img ... />）。

- HTMLParser.handle_data(data)：这个方法被用来处理任意数据。

- HTMLParser.handle_entityref(name)：处理 &name; 形式的命名字符引用（例如 &gt;）。

- HTMLParser.handle_charref(name)：用来处理 &#NNN; 和 &#xNNN; 形式的十进制和十六进制字符引用。

- HTMLParser.handle_comment(data)：在遇到注释的时候被调用

- HTMLParser.handle_decl(decl)：这个方法用来处理 HTML doctype 申明（例如 <!DOCTYPE html> ）。

- HTMLParser.handle_pi(data)：此方法在遇到处理指令的时候被调用。

- HTMLParser.unknown_decl(data)：当解析器读到无法识别的声明时，此方法被调用。

### requests

- requests.get('/url', params={'key': 'val'})

```py
import requests
r = requests.get('https://www.douban.com/',
                params={'q': 'python', 'cat': '1001'},
                headers={dict},
                data={dict}(post),
                json={dict},
                file={file: open('path', 'rb')},
                timeout=2.5 # 延时)

r.text
r.status_code
r.url
r.encoding
r.content # 二进制
r.json() # 直接获取json
```

### chardet

chardet.detect(data)

> {'encoding': 'utf-8', 'confidence': 0.99, 'language': ''}

### psutil

系统监控

- psutil.cpu_conut()：CPU 逻辑数量

- psutil.cpu_count(logical=False)：CPU 的物理核心

- psutil.cpu_times()：统计 cpu 的用户/系统/空闲时间

- psutil.virtual_memory()：获取物理内存

- psutil.swap_memory()：获取交换内存

- psutil.disk_patitions()：获取磁盘分区

- psutil.disk_usage('/')：获取磁盘使用情况

- psutil.disk_io_counters()： 磁盘 IO

- psutil.net_io_counters()：获取网络读写字节／包的个数

- psutil.net_if_addrs()：获取网络接口信息

- psutil.net_if_stats()：获取网络接口状态

- psutil.net_connections()：获取当前网路连接信息

- psutil.pids()：获取所有进程

- psutil.Process(pid).name()：进程名称

- psutil.Process(pid).exe()：进程路径

- psutil.Process(pid).cwd()：工作路径

- psutil.Process(pid).cmdline()：进程启动的命令行

- psutil.Process(pid).ppid()：父进程 ID

- psutil.Process(pid).parent()：父进程

## socket

```py
# client
import socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((ip, port))
s.send(b'content')
s.close()

# server
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind(('ip', port))
s.listen(num) # 最多允许多少个客户连接到服务器。
while True:
    con, addr = s.accept() # 返回socket对象和访问地址
    t = threading.Threading(target=cb, args=(con, addr))
    t.start()

def cb(con, addr):
    while True:
        cont = con.recv(1024)
        con.send('hello')
    con.close()
```

### pymysql

```py
import pymysql
conn = pymysql.connect(user='root', password='root', database='test')
cursor = conn.cursor()
cursor.execute('create table user (id varchar(20) primary key, name varchar(20))')
cursor.execute('insert in user(id, name) values ('1', 'lune')')
cursor.rowcount
cursor.commit()
cursor.close()

cursor1 = conn.cursor()
cursor1.execute('select * from user where id=%s', ('1',))
values = cursor.fetchall()
print(values)
```

### sqlalchemy
把关系数据库的表结构映射到对象上
```py
from sqlalchemy import Column, String, create_engine
from sqlalchemy.orm import sessionmaker
from sqlalchemy.declarvate import declarvate_base

# 数据库连接
Base = declarvate_base()

class User(Base):
    __tablename__ = 'user'
    id = Column(String(20), key='primary')
    name = Column(String(20))

engine = create_engine('mysql+pymysql://localhost:3366/test')
DBSession = sessionmaker(bind=engine)

# 表的操作，增加
usr = User(id='1', name='ming')
session = DBSession()
session.add(usr)
session.commit() # 提交即保存到数据库:
session.close()

# 表的查询
session2 = DBSession()
user = session2.query(User).filter(User.id='5').one()
print(user)
```

## web开发
> HTTP GET请求的格式：
* 每个Header一行一个，换行符是\r\n。
* 当遇到连续两个\r\n时，Header部分结束，后面的数据全部是Body。

> HTTP响应的格式：
* Body的数据类型由Content-Type头来确定

## 解释说明

```py
# 当模块被直接运行时，以下代码块将被运行，当模块是被导入时，代码块不被运行。
if __name__=='__main__':
    pass
```

## 爬虫记录

1. urllib 库的 request

```py
req = request.Request(url, headers={})
with request.urlopen(req) as f:
    res = f.read()
    res = res.decode('utf-8')
```

2. BeautifulSoup 获取节点
[爬虫-BeautifulSoup](https://www.cnblogs.com/zhaof/p/6930955.html)

```py
from bs4 import BeautifulSoup
soup = BeautifulSoup(res, 'html.parser')
titles = soup.findAll('a', class='title')
for title in titles:
    print(title.get_text())
```


3. selenium

4. 线程池访问连接列表


## 遇到的问题

1. vscode 终端和本地终端打印的环境变量不一致
   [解决方案](https://codeday.me/bug/20190627/1302940.html)
2. cmd + sft + b 执行代码，修改 task.json 中的 command 的路径


