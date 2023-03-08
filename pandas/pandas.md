## pandas 常用统计分析函数

数据分析中，pandas 库的常用数据运算函数：

| 函数           | 说明                         |
| -------------- | ---------------------------- |
| min()          | 计算最小值                   |
| max            | 计算最大值                   |
| sum            | 求和操作                     |
| mean           | 计算平均值                   |
| count          | 统计非缺失值个数             |
| size           | 统计元素个数                 |
| median         | 计算中位数                   |
| quantile       | 计算任意分位数               |
| var            | 计算方差                     |
| std            | 计算标准差                   |
| corr           | 计算相关系数                 |
| describe       | 描述性统计                   |
| info           | 数据信息                     |
| T              | 转置函数                     |
| groupby        | 分组                         |
| aggregate      | 聚合运算                     |
| shape          | 显示总行数、总列数           |
| value_counts() | 统计每一个不同的值的出现次数 |
| unqique()      | 显示唯一值                   |
| sort_values()  | 根据数据进行升序排列         |

#### read_csv

```py
pd.read_csv('文件路径',index_col=None) #indx_col=noet 用来指定表格的索引值

# 在默认为None的时候，pandas会自动将第一列作为索引，并额外添加一列。所以大多我们会使用index_col=0，直接将第一列作为索引，不额外添加列
```

#### 打印数据

head函数

```python

# 打印全体数据
print(df_data)
# 打印前5条数据
print(df_data.head())
# 打印前2条数据
print(df_data.head(2))
```

tail函数

```py
# 打印全体数据
print(df_data)
# 打印后5条数据
print(df_data.tail())
# 打印后2条数据
print(df_data.tail(2))
```

sample函数

```py
# 打印全体数据
print(df_data)
# 打印随机抽取的3条数据
print(df_data.sample(n=3))

# 查看索引
df_data.index
# 查看列名
df_data.columns
# 查看值
df_data.values
```

#### 统计和描述性方法

Pandas 还提供了统计和描述性方法，方便你从宏观的角度去了解数据集。`describe()` 相当于对数据集进行概览，会输出该数据集每一列数据的计数、最大值、最小值等。

```py
df.describe()
```

![7](图\7.png)

#### 数据项中缺失值

```py
data['name'].isnull()  #返回布尔值True
or
data.name.isnull()
```



#### 数据项中缺失值的总数量：

```python
data['name'].isnull().sum() #数据源[data['name'].isnull()].sum()   [data['name']数据源里的列
or
data.name.isnull().sum() #数据源.列名.isnull().sum()
```



#### 对缺失值进行平均值插补

```py
mean_val = data['rate'].mean() # mean() 平均值函数
data["rate"].fillna(mean_val, inplace=True) # inplace=True 修改源表数据
```



#### 对缺失值进行删除：

df.dropna()函数用于删除 dataframe 数据中的缺失数据，即 删除 NaN 数据 

```py
DataFrame.dropna(axis=0, how='any', thresh=None, subset=None, inplace=False)
```

| 参数名称 | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| axis     | 设置删除数据维度，0(行数据) 或 1(列数据) ，默认为 0(行)      |
| how      | 默认为 any(删除含有缺失值的行)，all(删除所有值都是缺失值的行) |
| thresh   | 接收int，保留至少有int个非空值的行                           |
| subset   | 接收ist，指定列删除缺失值                                    |
| inplace  | 布尔型，默认为false，是否对源数据源进行修改                  |

例：

```py
print("【对缺失评论作者数据项的那条记录进行删除：】")
data.dropna(subset=['author'], inplace=True) 
# subset 要处理的 列
```



####  数据项中的重复值

```
DataFrame.duplicated(subset=None, keep='first')
```

| 参数名称 | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| subset   | 定义哪些字段重复就属于重复值，默认是所有字段都重复           |
| keep     | 定义哪些数据属于重复值{first,last,false}，first是如果有重复数据，则第一条返回false，后面的重复数据显示为true; last与first相反，最后一条重复数据为false，其余重复数据都是true; false则所有重复值都为true。 |

```py
print("【查看数据集中存在重复行数的总数量：】")
display(data.duplicated().sum())

print("【分析重复值，返回一个布尔序列：】")
display(data.duplicated())
```



#### 去除重复值

去除重复值 检测 df 对象中的重复值 drop_duplicates()

df.drop_duplicates(subset=['name']), keep='first', inplace=True )

#### 修改数据类型

`astype()` 方法可以更改列的类型，下列公式将 Churn 离网率 特征修改为 `int64` 类型。

```py
df['Churn'] = df['Churn'].astype('int64')
```



#### 替换

当数量较大时,需要修改特定条件的数据时，可以使用替换函数

```py
#  将数据集中的“收货地址”字段中的“上海”替换为“上海市”
data['收货地址'] = data['收货地址'].replace('上海', '上海市')

data['收货地址'].loc[data['收货地址'] == '北京'] = '北京市'
```

#### 增减 DataFrame 的行列

##### insert()-添加列

`df.insert()` 方法需要三个参数：

- `loc`：表示插入的位置，即插入在数据框中的第几列。
- `column`：表示插入列的名称。
- `value`：表示插入列的数据。

```py
df.insert(loc=len(df.columns), column='Total calls', value=total_calls)
# loc 的值为 len(df.columns)，表示插入在数据框的最后一列。
#column 的值为 'Total calls'，表示插入列的名称。
#value 的值为 total_calls，表示插入列的数据。
```

##### 直接法

```py
df['Total charge'] = df['Total day charge'] + df['Total eve charge'] + \
    df['Total night charge'] + df['Total intl charge']
```

##### 删除行

```py
# 移除先前创捷的列
df.drop(['Total charge', 'Total calls'], axis=1, inplace=True)
# 删除行
df.drop([1, 2]).head()
#drop()：同上，这是一个 Pandas 函数，用于删除数据框中的某些行或列。

#[1, 2]：这是一个列表，指定了您要删除的行的索引。


```



##### 删除列

```py
# 删除第1列
data.drop('column_name', axis=1, inplace=True)

# 删除多列
data.drop(['column_name_1', 'column_name_2'], axis=1, inplace=True)

# 根据条件删除列，例如删除'Sales'列中值为0的列
data.drop('Sales', axis=1, inplace=True)

```

#### 重置索引

```py
data = data.reset_index(drop=True)  # 重置索引
```



#### data[ ] 与 data[data[ ]] 的区别：

```py
print("【打印出城市名称列为NaN的前5行：】")
pd.set_option("max_columns", None)
display(data['城市名称'].isnull().head(5)) # 返回布尔值
display(data[data['城市名称'].isnull()].head(5)) #返回行
```

结果如下：

```
【打印出城市名称列为NaN的前5行：】
0    True
1    True
2    True
3    True
4    True
Name: 城市名称, dtype: bool
    国家 省份名称                 更新时间 城市名称  城市确诊数量
0   中国   香港  2021-09-24 23:16:25  NaN     NaN
1   中国   中国  2021-09-24 23:16:25  NaN     NaN
2   美国   美国  2021-09-24 23:16:14  NaN     NaN
3   法国   法国  2021-09-24 23:16:14  NaN     NaN
4  比利时  比利时  2021-09-24 23:16:14  NaN     NaN
```

#### 索引

DataFrame 可以通过列名、行名、行号进行索引。`loc` 方法为通过名称索引，`iloc` 方法为通过数字索引。

#### 聚合统计

##### 一、value_counts

```py
>>>df = pd.DataFrame({
    'name': ['关羽', '张飞', '赵云', '张辽', '典韦', '甘宁'],
    'country': ['蜀', '蜀', '蜀', '魏', '魏', '吴']
})
print(df['country'].value_counts())

>>> 蜀    3
	魏    2
	吴    1
	Name: country, dtype: int64
```

以上实现其实仅适用于计数统计这种 特定需求，对于其他的聚合统计是不能满足的

##### 二、groupby

使用groupby()进行多条件聚合

```py
data.groupby(['name','xit'])['age'].mean()

```

##### 三、groupby+count

分组后对指定列聚合，在这种形式中依据country分组后只提取name一列，相当于每个country下对应了一个由多个name组成的series，而后的count即为对这个series进行count

```py
>>> df = pd.DataFrame({
    'name': ['关羽', '张飞', '赵云', '张辽', '典韦', 	'甘宁'],
    'country': ['蜀', '蜀', '蜀', '魏', '魏', '吴']
	})
	print(df.groupby('country')['name'].count())
    
>>> country
	吴    1
	蜀    3
	魏    2
	Name: name, dtype: int64
```

df.groupby('country').count()

```py
df = pd.DataFrame({
    'name': ['关羽', '张飞', '赵云', '张辽', '典韦', '甘宁'],
    'country': ['蜀', '蜀', '蜀', '魏', '魏', '吴'],
    'sex':['男','男','男','女','男','女',]
})
print(df.groupby('country').count())

>>>country    name  sex     
	吴           1    1
	蜀           3    3
	魏           2    2
```

##### 四、groupby+agg

agg函数主要接收两个参数，第一个参数func用于接收聚合算子，可以是一个函数名或对象，也可以是一个函数列表，还可以是一个字典，使用方法很是灵活；

第二参数axis则是指定聚合所沿着的轴向，默认是axis=0，即沿着行的方向对列聚合。具可定制性。

```py
>>>df = pd.DataFrame({
    'name': ['关羽', '张飞', '赵云', '张辽', '典韦', 	'甘宁'],
    'country': ['蜀', '蜀', '蜀', '魏', '魏', '吴'],
    'sex': ['男', '男', '男', '女', '男', '女', ]
	})

print(df.groupby('country').agg('count')['name'])
# 或
print(df.groupby('country')['name'].agg('count'))

>>>country
	吴    1
	蜀    3
	魏    2
	Name: name, dtype: int64
    

```

agg内接收聚合函数字典，其中key为列名，value为聚合函数或函数列表，可实现同时对多个不同列实现不同聚合统计。

这里字典的key是要聚合的name字段，字典的value即为要用的聚合函数count，当然也可以是包含count的列表的形式。

用字典传入聚合函数的形式下，统计结果都是一个dataframe，更进一步的说当传入字典的value是聚合函数列表时，结果中dataframe的列名是一个二级列名。

![1](图\1.png)

![2](图\2.webp)

agg内接收新列名+元组，实现对指定列聚合并重命名。

对于聚合函数不是特别复杂而又希望能同时完成聚合列的重命名时，可以选用此种方式，具体传参形式实际上采用了python中可变字典参数**kwargs的用法，其中字典参数中的key是新列名，value是一个元组的形式，包括聚合字段列名和聚合函数.

![3](图\3.webp)

##### 五、groupby+apply

 在上述方法中，groupby('country')后的结果，实际上是得到了一个DataFrameGroupBy对象，实际上是一组(key, value)的集合，其中每个key对应country列中的一种取值，每个value为该key对应的一个子dataframe

```py
>>>df = pd.DataFrame({
    'name': ['关羽', '张飞', '赵云', '张辽', '典韦', 	'甘宁'],
    'country': ['蜀', '蜀', '蜀', '魏', '魏', '吴'],
    'sex': ['男', '男', '男', '女', '男', '女', ]
	})
print(df.groupby('country').apply(lambdasdf:sdf['name'].count()))

>>>country
	吴    1
	蜀    3
	魏    2
	dtype: int64
```

#### apply函数

**分隔**

```py
print(data['date'])
data["date"] = data["date"].apply(lambda x: str(x).split(" ")[0])
print('----------------------------------------------------------------')
print(data['date'])
```

![4](图\4.png)

**替换**

![5](图\5.png)

将性别sex列转化为0和1数值，其中female对应0，male对应1。应用apply函数实现这一功能非常简单：

```py
titanic['sex_num'] = titanic['sex'].apply(lambda x: 1 if x == 'male' else 0)
titanic.head()
```

![6](图\6.png)





1.Pandas数据结构：Series和DataFrame 

2.Pandas数据操作：索引、选择、过滤、排序、重塑、合并、组合 

3.Pandas数据分析：统计、绘图、描述性统计 

4.Pandas数据处理：缺失值处理、数据转换、数据聚合

5.Pandas数据文件读写：csv、excel、json、html等



### 杂类

#### 1、去除索引多余内容

```py
data = pd.read_excel('../pyecharts/数据集/timeline.xlsx',index_col=0) # 将月份设置为索引
```

![9](图\9.png)

删除年份

```py
data.index = data.index.str.split('年').str[1]
```

效果：

![10](C:\Users\admin\Desktop\笔记\pandas\图\10.png)
