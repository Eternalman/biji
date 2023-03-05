### os模块的常用方法

**os.listdir()**--打印路径

```py
os.listdir() # 列出（当前）目录下的全部路径（及文件）
```

**os.mkdir()**--创建单个路径

```py
os.mkdir() # 用处是“新建一个路径”，只能在已有的路径下新建一级路径，否则（即新建多级路径）会抛出异常需要传入一个类路径参数 用以指定新建路径的位置和名称,如果存则会报错。
```

**os.rename()**--将文件或路径重命名

```py
os.rename(src, dst) # 即将 src 指向的文件或路径重命名为 dst 指定的名称
```

**os.makedirs()**--创建多个路径

**os.remove()**--删除文件

  如果指定路径是目录而非文件的话，会抛出异常。

**os.rmdir()**--删除目录

**os.linesep**--换行

**os.getcwd()**--获取当前路径

**os.pardir**--返回当前目录的父目录

**os.chdir()**--切换到指定路径

```py
os.chdir(路径) # 如果路径不存在，则抛出异常
```

### os.path 模块

**os.path.join()**--组合路径

如果传入路径中存在一个“绝对路径”格式的字符串，且这个字符串不是函数的第 一个参数，那么其他在这个参数之前的所有参数都会被丢弃，余下的参数再进行组 合。

更准确地说，只有最后一个“绝对路径”及其之后的参数才会体现在返回结果中

```py
>>> os.path.join("just", "do", "python", "dot", "com")
'just\\do\\python\\dot\\com'
>>> 
>>> os.path.join("just", "do", "d:/", "python", "dot", "com")
'd:/python\\dot\\com'
>>> 
>>> os.path.join("just", "do", "d:/", "python", "dot", "g:/", "com")
'g:/com'
```

**os.path.dirname()**--返回的是最后一个分隔符前的整个字符串

```py
>>> os.path.dirname("/ityouknow/justdopython/IAmBasename")
'/ityouknow/justdopython'
>>> 
>>> os.path.dirname("/ityouknow/justdopython/IAmBasename/")
'/ityouknow/justdopython/IAmBasename'
```

**os.path.split()**--路径分割

函数 os.path.split()的功能就是将传入路径以最后一个分隔符为界，分成两个字符串，并打包成元组的形式返回

```py
>>>name = r'C:\Users\Administrator\Desktop\1111111\04 数据处理\08 工程代码\PythonTask08'
	a = os.path.split(name)
    print(a)
	print(a[0])
	print(a[1])
返回值
('C:\\Users\\Administrator\\Desktop\\1111111\\04 数据处理\\08 工程代码', 'PythonTask08')
C:\Users\Administrator\Desktop\1111111\04 数据处理\08 工程代码
PythonTask08
```

**os.path.splitext()**--文件分割

将文件名和后缀名分成两个字符串，并打包成元组的形式返回

```py
>>>name = '我的文档.txt'
	a= os.path.splitext(name)
	print(a)
	print(a[0])
	print(a[1])
>>>('我的文档', '.txt')
我的文档
.txt
```

**os.path.exists()**--判断路径是否存在

若存在则返回 True，不存在则返 回 False

```py
>>> os.path.exists(".")
True
>>> os.path.exists("./just")
True
>>> os.path.exists("./Inexistence") # 不存在的路径
False
```

**os.path.isabs()**--判断是否是绝对路径

```py
>>> os.path.isabs("a:/justdopython")
True
```

**os.path.isfile()** 和 **os.path.isdir()**

这两个函数分别判断传入路径是否是文件或路径

```py
>>> # 无效路径
>>> os.path.isfile("a:/justdopython")
False
>>> 
>>> # 有效路径
>>> os.path.isfile("./just/plain_txt")
True
>>> 
>>> # 无效路径
>>> os.path.isdir("a:/justdopython/")
False
>>> # 有效路径
>>> os.path.isdir("./just/")
True
```

