## Numpy 常用函数

* 数组对象的一些方法
* data.size

| 方法  | 说明                                       |
| ----- | ------------------------------------------ |
| shape | 返回该数组形状 也就是几行几列，参考：(2,3) |
| size  | 返回该元素个数                             |
| ndim  | 输出该数组维度，返回类型为整数             |
| dtype | 返回该数组类型                             |

***

### numpy的创建数组

| 方法          | 说明                                                         |
| ------------- | ------------------------------------------------------------ |
| np.array()    | 将输入的列表，元组等可迭代对象转换为数组                     |
| np.arange()   | 类似range()的一种创建数组的一种方式，返回一维数组            |
| np.linspace() | 均匀返回一个范围内的等差数组，举例：np.linspace(1,10,10) 会均匀返回1到10的10个元素 |
| np.empty()    | 根据给定的数量和维度，返回一组随机浮点数                     |
| np.zeros()    | 根据给定长度以及形状生成一组全是0的数组                      |
| np.ones()     | 根据给定长度以及形状生成一组全是1的数组                      |

* np.array()

  ```
  data = np.array([10,20,30,40]) ## 创建二维数组
  结果 : [10 20 30 40]
  
  ##也可以创建二维数组等
  data = np.array([
  		[1,2,3,4,5],
  		[11,12,13,14,15],
  		[21,22,23,24,25]
  		]
  		)
  结果：
  [[ 1  2  3  4  5]
   [11 12 13 14 15]
   [21 22 23 24 25]]
  ```

  

## Numpy通用函数

### 1、mean()函数

mean()函数用于计算一个数组中元素中元素的算术平均值

```py
numpy.mean(a, axis=None)
# a: numpy数组
# axis: 计算的轴向 0 表示求每列的平均值， 1表示求每行平均值
```

------

### 2、average()函数

average()函数用于求一个数组中的元素的加权平均值

```py
numpy.average(a, axis=None, weights=None)
# a: numpy数组
# axis: 计算的轴向 0 表示求每列的平均值， 1表示求每行平均值
# weights:权重，默认情况下会为要计算加权平均值的数组元素分配相等的权重
```

------

### 3、sum()函数

sum()函数用于求一个数组的和

```py
numpy.sum(a, axis=None)
# a: numpy数组
# axis：计算的轴向
```

------

### 4、max()函数

max()函数用于求一个数组的最大值

```python
numpy.sum(a, axis=None)
```

------

### 5、max()函数

max()函数用于求一个数组的最大值

```py
numpy.max(a, axis=None)
```

------

### 6、argmax()函数

argmax()函数用于求一个数组的最大值的下标, 当数组中有多个最大值时,则获取第一个最大值的下标。

```py
numpy.argmax(a, axis=None)

```

------

### 7、median()函数

median()函数用于求一个数组的中位数

```py
numpy.median(a, axis=None)
```

------

### 8、var()函数

var()函数用于求一个数组的方差。方差是用数组中的各项-平均值的平方求和后再除以数组的长度。

```py
numpy.var(a, axis=None, ddof=0)

# ddof：非自由度,默认为0,求出来的是总体方差,如果该参数为1,则求出来的是样本方差
```

------

### 9、loadtxt()函数

loadtxt()函数为用于读取数据。

```py
loadtxt(fname, dtype=float, delimiter=None, converters=None, usecols=None, unpack=False)

# fname：文件路径。
# dtype：元素类型，默认为float。
# delimiter：分隔符，默认为一个空格。
# converters：转换器字典，键为列索引，值为转换函数，它会将读取到的数据通过函数转换后，再返回。
# usecols：需要读取的列，默认读取所有的列。
# unpack：是否展开，默认为False，不展开，如果设置为True，可以拿到每一列的数据。
```

------

### 10、maximum()/minimum()

maximum()/minimum()函数用于将两个同维数组中对应元素中的最大/最小元素构成一个新的数组

```py
numpy.maximum(x1,x2)
# x1：numpy数组
# x2:numpy数组,维度必须与x1一致
```

------

### 11、std()函数

std()函数用于求一个数组中元素的标准差，标准差即方差开方

```py
numpy.std(a, axis=None（-1，0，1）, ddof=0)
# ddof:非自由度,默认为0,计算得出的是总体标准差
```

------

### 12、sort()函数

sort()函数用于对numpy数组进行排序

```py
numpy.sort(a,axis=-1, kin='quicksort')
# axis: 要排序的维度,默认值为-1 ，即按照最后一个维度排序
# kind: 排序类型， quicksort 为快速排序,mergesort为归并排序,heapsort为堆排序
```

------

## NumPy字符串处理

### 1、**add()**函数

add函数用于字符串拼接

```py
np.char.add(['hello'], ['world'])

# 运行结果为：
array(['helloworld'], dtype='<U10')
```

### 2、multiply()函数

multiply()函数用于多次重复数组中的元素

```PY
np.char.multiply()

np.char.multiply('hello',3)
# 运行结果
array('hellohellohello', dtype='<U15')
```

### 3、center()函数

center函数用于字符串居中

```PY
np.char.center('hello', 20, fillchar='*')

# 运行结果为：
array('*******hello********', dtype='<U20')
```

### 4、lower()函数和upper()函数

lower()和upper()用于将字符串转为小写/大写

```py
np.char.lower(['I', 'LIKE', 'CHINA'])
# 运行结果为：
array(['i', 'like', 'china'], dtype='<U5')

np.char.upper(['i', 'like', 'china'])
# 运行结果为：
array(['I', 'LIKE', 'CHINA'], dtype='<U5')
```

### 5、split()函数

split()用于分割字符串

```py
np.char.split('do you like me?')  # 默认按空格分隔
# 运行结果为：
array(list(['do', 'you', 'like', 'me?']), dtype=object)
----------------------------------------------------------------------------
np.char.split('yes,i like you,very much', sep=',') # 按逗号分隔
# 运行结果为：
array(list(['yes', 'i like you', 'very much']), dtype=object)
```

### 6、split()函数

split()用于移除左右两侧的字符

```py
np.char.strip('  \r\nabcd\t  ')  # 移除左右空白字符
运行结果为：
array('abcd', dtype='<U11')
----------------------------------------------------------------------------
np.char.strip('abca', 'a')  # 移除左右的a字符
运行结果为：
array('bc', dtype='<U4')
```

### 7、join()函数

join用于字符串的拼接

```py
np.char.join(':', 'hello')
# 运行结果为：
array('h:e:l:l:o', dtype='<U9')
---------------------------------------------------------------
np.char.join([':', '-'], ['hello', 'world'])
运行结果为：
array(['h:e:l:l:o', 'w-o-r-l-d'], dtype='<U9')
```

