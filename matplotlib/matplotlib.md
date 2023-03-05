### *中文及负号问题

```py
plt.rcParams['font.sans-serif'] = 'SimHei' # 用于正常中文标签
plt.rcParams['axes.unicode_minus']=False #用于正常显示负号
```

### 创建画布

##### figure：创建

```python
plt.figure(figsize=(20,8),dpi = 100)
```

##### figsize：画布大小

#### 图像类型

```py
plot.plot() # 折线图
plot.bar() # 柱形图
plot.pie() # 饼图
plot.scatter() #散点图 
plot.hist() # 二维条形图，显示数据的分配情况
plot.boxplot() # 箱型图
```

#### 刻度与标签

**xlabel()** 和 **ylabel()** 方法给 X 轴和 Y 轴添加标签，通过 **title()** 方法为图表添加标题

```py
plt.xlabel('Amounts')
plt.title('Example')
plt.ylabel('name')
```

plt.title() 设置标题 

常用函数数:

fontsize 设置字体大小

fontweight 设置字体粗细

fontstyle 设置字体类型

verticalalignment 设置水平对齐方式 ， 可选数： ： 'center' , 'top' , 'bottom' ,'baseline' 

horizontalalignment 设置垂直对齐 方式，可选参数：left,right,center 

rotation(旋转角度)可选参数 为:vertical,horizontal 也可以为数字 

alpha 透明度，参数值 0 至 1 之间 

backgroundcolor 标题背景颜色

#### x、y轴的刻度和刻度值

x\y xlim() --设置x、y坐标轴范围 

```py
plt.ylim(ymin=0, ymax=300)  # ylim 是y轴的刻度，ymin是最小值，ymax是最大值
```

x、y label() --设置x坐标轴名称

x、y ticks() --设置x、y轴刻度

```py
plt.yticks(ticks=(0, 100, 200))  # yticks 是y轴点刻度标签， y标签只有0，100，200
```



#### 图例

在 **bar** 函数中传入 **label** 参数表示图例名称，通 过 **legend** 函数即可绘制出图例

```py
data1=[23,85,72,43,52]
data2=[42,35,21,16,9]
width=0.3
plt.bar(np.arange(len(data1)),data1,width=width,label='one')
plt.bar(np.arange(len(data2))+width,data2,width=width,label='two')
plt.legend() 
plt.show()
```

![image-20221219181026432](C:\Users\Administrator\Desktop\matplotlib\图\图例.png)

plt.legend(loc='')  # 指定位置
参数有：

| 位置     | stying       | Number |
| -------- | ------------ | ------ |
| 右上     | upper right  | 1      |
| 左上     | upper left   | 2      |
| 左下     | lower left   | 3      |
| 右下     | lower right  | 4      |
| 正右     | right        | 5      |
| 中央偏左 | center left  | 6      |
| 中央偏右 | center right | 7      |
| 中央偏下 | lower center | 8      |
| 中央偏上 | upper center | 9      |
| 正中央   | center       | 10     |

![2](图\2.png)

####  文本注解

通过 text 函数可以在指定的坐标（x,y）上加入文本注释

```py
for x,y in zip(range(len(data)),data):
plt.text(x,y,y,ha='center',va='bottom') #文本注解 # 第一个参数是x 轴坐，# 第二个参数是 y 轴坐标，# 第三个参数是要显式的内容
```

#### 线条形状设置

线条形状设置  **linestyle**    or **ls**

| 线条风格linestyle 或ls | 描述   | 线条风格 | 描述 |
| ---------------------- | ------ | -------- | ---- |
| '-'                    | 实线   | ':'      | 虚线 |
| '_'                    | 破折线 |          |      |
| '-.'                   | 点划线 |          |      |

#### 对坐标点的标记（线条标记）

marker：对坐标点标记（线条标记）

| 标记 maker | 描述    | 标记 | 描述             |
| ---------- | ------- | ---- | ---------------- |
| 'o'        | 圆圈    | '.'  | 点               |
| 'D'        | 菱形    | 's'  | 正方形           |
| 'h'        | 六边形1 | '*'  | 星号             |
| 'H'        | 六边形2 | 'd'  | 小菱形           |
| '_'        | 水平线  | 'v'  | 一角朝下的三角形 |
| '8'        | 八边形  | '<'  | 一脚朝左的三角形 |
| 'p'        | 五边形  | '>'  | 一角朝右的三角形 |
| ','        | 像素    | '^'  | 一角朝上的三角形 |
| '+'        | 加号    | '\'  | 竖线             |

#### 颜色设置

| 别名 | 颜色   | 别名 | 颜色 |
| ---- | ------ | ---- | ---- |
| b    | 蓝色   | g    | 绿色 |
| r    | 红色   | y    | 黄色 |
| c    | 青色   | k    | 黑色 |
| m    | 洋红色 | w    | 白色 |

#### 'font  字体集、字体大小和样式设置等

##### fontsize--设置水平对齐方式

```py
fontsize='11' # 设置字体大小
```

grid  设置网格颜色和线性

line 设置线条（颜色、线性、宽度等）和标记

#### 线型图

```py
date.plot(kind='line')
```

#### 柱状图

```py
matplotlib.pyplot.bar(x, height, width=0.8, bottom=None, *, align='center', data=None, **kwargs)
```

**x**：浮点型数组，柱形图的 x 轴数据。

**height**：浮点型数组，柱形图的高度。

**width**：浮点型数组，柱形图的宽度。

**bottom**：浮点型数组，底座的 y 坐标，默认 0。

**align**：柱形图与 x 坐标的对齐方式，'center' 以 x 位置为中心，这是默认值。 'edge'：将柱形图的左边缘与 x 位置对齐。要对齐右边缘的条形，可以传递负数的宽度值及 align='edge'。

#### 饼图

```py
matplotlib.pyplot.pie(x, explode=None, labels=None, colors=None, autopct=None, pctdistance=0.6, shadow=False, labeldistance=1.1, startangle=0, radius=1, counterclock=True, wedgeprops=None, textprops=None, center=0, 0, frame=False, rotatelabels=False, *, normalize=None, data=None)[source]
```

**x**：浮点型数组，表示每个扇形的面积。

**explode**：数组，表示各个扇形之间的间隔，默认值为0。

**labels**：列表，各个扇形的标签，默认值为 None。

**colors**：数组，表示各个扇形的颜色，默认值为 None。

**autopct**：设置饼图内各个扇形百分比显示格式，**%d%%** 整数百分比，**%0.1f** 一位小数， **%0.1f%%** 一位小数百分比， **%0.2f%%** 两位小数百分比。

**startangle：**：起始绘制饼图的角度，默认为从 x 轴正方向逆时针画起，如设定 =90 则从 y 轴正方向画起。

**counterclock**：布尔值，设置指针方向，默认为 True，即逆时针，False 为顺时针。

#### 散点图

```py
matplotlib.pyplot.scatter(x, y, s=None, c=None, marker=None, cmap=None, norm=None, vmin=None, vmax=None, alpha=None, linewidths=None, *, edgecolors=None, plotnonfinite=False, data=None, **kwargs)
```

**x，y**：长度相同的数组，也就是我们即将绘制散点图的数据点，输入数据。

**s**：点的大小，默认 20，也可以是个数组，数组每个参数为对应点的大小。

**c**：点的颜色，默认蓝色 'b'，也可以是个 RGB 或 RGBA 二维行数组。

**marker**：点的样式，默认小圆圈 'o'。

**cmap**：颜色条，只有 c 是一个浮点数数组的时才使用。如果没有申明就是 image.cmap。

**norm**：Normalize，默认 None，数据亮度在 0-1 之间，只有 c 是一个浮点数的数组的时才使用。

**vmin，vmax：**：亮度设置，在 norm 参数存在时会忽略。

**alpha：**：透明度设置，0-1 之间，默认 None，即不透明。

**linewidths：**：标记点的长度。

**edgecolors：**：颜色或颜色序列，默认为 'face'，可选值有 'face', 'none', None。

**plotnonfinite：**：布尔值，设置是否使用非限定的 c ( inf, -inf 或 nan) 绘制点。