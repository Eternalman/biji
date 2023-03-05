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

  