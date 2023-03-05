#### 全局配置和系列配置

导入设置系列配置和全局配置

```py
from pyecharts import options as opts
```

##### set_global_opts  全局配置设置

![0](图/0.png)



###### 初始化配置项

init_opts=opts.InitOpts()---初始化配置项

放在Bar()或者Line()里

|      参数      | 说明                                                         |
| :------------: | ------------------------------------------------------------ |
|     width      | 图表画布宽度，css 长度单位。                                 |
|     height     | 图表画布高度，css 长度单位。                                 |
|    chart_id    | 图表 ID，图表唯一标识，用于在多图表时区分                    |
|   page_title   | 网页标题                                                     |
|     theme      | 图表主题                                                     |
|    bg_color    | 图表背景颜色                                                 |
|    js_host     | 远程 js host，如不设置默认为 https://assets.pyecharts.org/assets/" |
| animation_opts | 画图动画初始化配置                                           |



###### 标题配置项

title_opts=opts.TitleOpts() ---标题配置项

|          参数           | 说明                               |
| :---------------------: | :--------------------------------- |
|          title          | 表示主标题文本                     |
|        subtitle         | 表示副标题文本                     |
|        item_gap         | 表示主副标题之间的间距。默认为10   |
|        pos_left         | title 组件离容器左侧的距离。       |
|        pos_right        | title 组件离容器右侧的距离。       |
|  title_textstyle_opts   | 表示主标题字体样式配置项--系列配置 |
| subtitle_textstyle_opts | 表示副标题字体样式配置项--系列配置 |



###### 图列配置项

legend_opts=opts.LegendOpts()

| 参数             | 说明                                                         |
| ---------------- | ------------------------------------------------------------ |
| is_show          | 是否显示图例组件                                             |
| type_            | 图例的类型； 'plain'：普通图例、'scroll'：可滚动翻页的图例   |
| pos_left/right   | 图例组件离容器左/右侧的距离                                  |
| pos_top/bottom   | 图例组件离容器上/下侧的距离                                  |
| orient           | 图例列表的布局朝向；'horizontal', 'vertical'(水平、垂直)     |
| align            | 图例标记和文本的对齐,默认自动；可选参数: `auto`, `left`, `right` |
| inactive_color   | 图例关闭时的颜色。默认是 #ccc                                |
| padding          | 图例内边距，单位px，默认各方向内边距为5                      |
| item_gap         | 图例每项之间的间隔；默认间隔为 10                            |
| item_width/heigh | 图例标记的图形宽度/高度，默认为25、14                        |
| selected_mode    | 图例选择的模式，控制是否可以通过点击图例改变系列的显示状态，false关闭，single、multiple(单项、多选) |
| textstyle_opts   | 图例组件字体样式                                             |



###### 提示框的配置项

tooltip_opts=opts.TooltipOpts()

| 参数                   | 说明                                                         |
| :--------------------- | ------------------------------------------------------------ |
| is_show                | 是否显示提示框组件                                           |
| axis_pointer_type      | 指示器类型；'line'：直线指示器；'shadow'：阴影指示器 ；'none'：无指示器；'cross'：十字准星指示器 |
| is_show_content        | 是否显示提示框浮层，默认显示                                 |
| is_always_show_content | 是否永远显示提示框内容，默认为False                          |
| show_delay             | 浮层显示的延迟，单位为 ms，默认没有延迟，也不建议设置        |
| hide_delay             | 浮层隐藏的延迟，单位为 ms，在 alwaysShowContent 为 true 的时候无效 |
| position               | 提示框浮层的位置，默认不设置时位置会跟随鼠标的位置           |
| border_color           | 提示框浮层的边框颜色                                         |
| border_width           | 提示框浮层的边框宽                                           |
| textstyle_opts         | 文字样式配置项                                               |
| trigger                | 触发类型；'item'(数据项图形触发,主要在散点图，饼图等无类目轴的图表中使用)、'axis'(坐标轴触发,柱状图，折线图等会使用类目轴的图表中使用)、'none'(什么都不触发) |
| trigger_on             | 提示框触发的条件，'mousemove': 鼠标移动时触发，'click': 鼠标点击时触发，'mousemove\|click': 同时鼠标移动和点击时触发，'none': 不在 'mousemove' 或 'click' 时触发 |



###### 视觉映射配置

visualmap_opts=opts.VisualMapOpts()

|       参数        | 说明                                                         |
| :---------------: | ------------------------------------------------------------ |
|      is_show      | 是否显示视觉映射配置                                         |
|       type_       | 映射过渡类型，可选，"color", "size"                          |
|    min_ / max_    | 指定 visualMapPiecewise 组件的最小/最大值                    |
|    range_text     | 两端的文本，如['High', 'Low']                                |
|    range_color    | visualMap 组件过渡颜色                                       |
|    range_size     | visualMap 组件过渡 symbol 大小                               |
|   range_opacity   | visualMap 图元以及其附属物（如文字标签）的透明度             |
|   is_piecewise    | 是否为分段型，默认为False                                    |
|   split_number    | 连续型数据，自动平均切分成几段。默认为5段。连续数据的范围需要 max 和 min 来指定 |
|      orient       | 放置 visualMap 组件，水平（'horizontal'）或者竖直（'vertical'） |
| item_width/height | 图形的宽度/高度，即长条的宽度、高度                          |
|    is_inverse     | 是否反转 visualMap 组件，默认为 False                        |
|   is_calculable   | 是否显示拖拽用的手柄（手柄能拖拽调整选中范围），默认是 True  |
|  pos_left/right   | visualMap 组件离容器左/右侧的距离；'left', 'center', 'right' |
|  pos_top/bottom   | visualMap 组件离容器上/下侧的距离；'top', 'middle', 'bottom' |
|   series_index    | 指定取哪个系列的数据，默认取所有系列                         |
|     dimension     | 组件映射维度                                                 |
| background_color  | visualMap 组件的背景色                                       |
|   border_color    | visualMap 组件的边框颜色                                     |
|   border_width    | visualMap 边框线宽，单位px                                   |
|   out_of_range    | 定义 在选中范围外 的视觉元素。（用户可以和 visualMap 组件交互，用鼠标或触摸选择范围） |
|  textstyle_opts   | 文字样式配置项                                               |



###### 区域缩放配置项

datazoom_opts=opts.DataZoomOpts()

| 参数           | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| is_show        | 是否显示组件，false不会显示，但是数据过滤的功能还存在        |
| type_          | 组件类型，可选 "slider", "inside"（滑块，内部）              |
| is_realtime    | 拖动时,是否实时更新系列的视图。如果设置为false，则只在拖拽结束的时候更新，默认为True |
| orient         | 布局方式是横还是竖；可选值为：'horizontal', 'vertical'(水平、垂直) |
| pos_left/right | 组件离容器左/右侧的距离                                      |
| pos_top/bottom | 组件离容器上/下侧的距离                                      |
| range_start    | 数据窗口范围的起始百分比。范围是：0 ~ 100。表示 0% ~ 100%。  |
| range_end      | 数据窗口范围的结束百分比。范围是：0 ~ 100                    |
| start_value    | 数据窗口范围的起始数值。如果设置了 start 则 startValue 失效  |
| end_value      | 数据窗口范围的结束数值。如果设置了 end 则 endValue 失效      |
| is_zoom_lock   | 是否锁定选择区域（或叫做数据窗口）的大小                     |
| filter_mode    | 当前数据窗口外的数据，被过滤掉                               |



###### 坐标轴配置项

x/y axis_opts=opts.AxisOpts() 

|         参数          | 说明                                                         |
| :-------------------: | :----------------------------------------------------------- |
|        is_show        | 是否显示 x /y轴。默认为True                                  |
|      is_inverse       | 表示是否反向坐标轴。默认为False                              |
|         name          | 表示坐标轴名称                                               |
|      name_rotate      | 坐标轴名字旋转，角度值                                       |
|     name_location     | 坐标轴名称显示位置。可选：默认end  'start[开始]'、'middle'[中间] 、'center[中间]'、'end[结束]' |
|      name_rotat       | 表示坐标轴名字旋转角度值。默认为None                         |
|       name_gap        | 表示坐标轴名称与轴线之间的距离。默认为15                     |
|       position        | 表示X轴的位置，可选top、bottom，top表示在上侧，bottom表示在下侧。默认为None |
|     split_number      | 表示坐标轴的分割段数。默认为5                                |
|         min_          | 表示坐标轴刻度最小值。默认为None                             |
|         max_          | 表示坐标轴刻度最大值。默认为None                             |
|       interval        | 自动计算的坐标轴间隔大小                                     |
|     min_interval      | 自动计算的坐标轴最小间隔大小                                 |
|     max_interval      | 自动计算的坐标轴最大间隔大小                                 |
|         type_         | 坐标轴类型；'value': 数值轴，适用于连续数据。 'category': 类目轴，适用于离散的类目数据。 'time': 时间轴，适用于连续的时序数据。'log' 对数轴。适用于对数数据。 |
|                       |                                                              |
|     axisline_opts     | 坐标轴刻度线(轴线)配置项                                     |
|     axistick_opts     | 坐标轴刻度配置项                                             |
|   axispointer_opts    | 坐标轴指示器配置项                                           |
|    axislabel_opts     | 坐标轴标签配置项                                             |
|                       |                                                              |
|  name_textstyle_opts  | 坐标轴名称的文字样式                                         |
|    splitarea_opts     | 分割区域配置项                                               |
|    splitline_opts     | 分割线配置项                                                 |
|    minor_tick_opts    | 坐标轴次刻度线相关设置                                       |
| minor_split_line_opts | 坐标轴在 grid 区域中的次分隔线。次分割线会对齐次刻度线 minorTick |
|                       |                                                              |



###### 坐标轴轴线配置项

全局配置中设置

x/yaxis_opts=opts.AxisOpts(axisline_opts=)

| 参数               | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| is_show            | 是否显示坐标轴线                                             |
| is_on_zero         | X 轴或者 Y 轴的轴线是否在另一个轴的 0 刻度上，只有在另一个轴为数值轴且包含 0 刻度时有效。 |
| on_zero_axis_index | 当有双轴时，可以用这个属性手动指定，在哪个轴的 0 刻度上      |
| **linestyle_opts** | 坐标轴线风格配置项                                           |
| symbol             | 轴线两边的箭头。可以是字符串，表示两端使用同样的箭头；或者长度为 2 的字符串数组，分别表示两端的箭头 |



###### 坐标轴刻度配置项

x/yaxis_opts=opts.AxisOpts(axisline_opts=)

| 参数                | 说明                                                         |
| ------------------- | ------------------------------------------------------------ |
| is_show             | 是否显示坐标轴刻度                                           |
| is_inside           | 坐标轴刻度是否朝内，默认朝外                                 |
| length              | 坐标轴刻度的长度                                             |
| **linestyle_opts**  | 坐标轴线风格配置项                                           |
| is_align_with_label | 类目轴中在 boundaryGap 为 true 的时候有效，可以保证刻度线和标签对齐 |



###### 坐标轴指示配置项

x/yaxis_opts=opts.AxisOpts(axispointer_opts=)

| 参数           | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| is_show        | 默认显示坐标轴指示器                                         |
| type_          | 指示器类型；'line' 直线指示器 、'shadow' 阴影指示器、'none' 无指示器 |
| label          | 坐标轴指示器的文本标签，坐标轴标签配置项                     |
| linestyle_opts | 坐标轴线风格配置项                                           |
| link           | 同轴的 axisPointer 可以进行联动，在这里设置                  |



###### 工具箱配置项

toolbox_opts=opts.ToolboxOpts()

|    参数    | 说明                                                         |
| :--------: | ------------------------------------------------------------ |
|  is_show   | 是否显示工具栏组件，默认为True                               |
|   orient   | 工具栏 icon 的布局朝向；'horizontal', 'vertical'(水平，垂直) |
|  pos_left  | 工具栏组件离容器左侧的距离。可以是像 '20%' 这样相对于容器高宽的百分比 |
| pos_right  | 可以是像 '20%' 这样相对于容器高宽的百分比。                  |
|  pos_top   | 工具栏组件离容器上侧的距离。                                 |
| pos_bottom | 工具栏组件离容器下侧的距离。                                 |
|  feature   | 各工具配置项，feature=opts.ToolBoxFeatureOpts()              |



###### 工具箱各工具配置项

|     参数      | 说明                                                         |
| :-----------: | :----------------------------------------------------------- |
| save_as_image | 保存为图片                                                   |
|    restore    | 配置项还原                                                   |
|   data_view   | 数据视图工具，可以展现当前图表所用的数据，编辑后可以动态更新 |
|   data_zoom   | 数据区域缩放。（目前只支持直角坐标系的缩放）                 |
|  magic_type   | 动态类型切换                                                 |
|     brush     | 选框组件的控制按钮                                           |

![1](图\1.png)



##### set_series_opts  系列配置设置

###### 标签配置项

axislabel_opts=label_opts=opts.LabelOpts()

label_opts=opts.LabelOpts() ---标签配置项

在全局配置下的作用是标签数值的样式( 1月、2月 )

|       参数       | 说明                                                         |
| :--------------: | :----------------------------------------------------------- |
|     is_show      | 是否显示标签，默认为True                                     |
|    font_size     | 文字的字体大小                                               |
|      color       | 文字的颜色。# 如果设置为 'auto'，则为视觉映射得到的颜色，如系列色。 |
|     position     | 标签的位置，'top'，'left'，'right'，'bottom'，'center ','inside' |
|     distance     | 距离图形元素的距离。（如 'top'、'insideRight'）时候有效。    |
|    font_style    | 文字字体的风格      \# 文字字体的风格，可选：    # 'normal'，'italic'，'oblique' |
|   font_weight    | 文字字体的粗细      \# 文字字体的粗细，可选：    # 'normal'，'bold'，'bolder'，'lighter' |
|      rotate      | 标签旋转。从 -90 度到 90 度。正值是逆时针。                  |
|      margin      | 刻度标签与轴线之间的距离，数值越大离坐标轴越远               |
| horizontal_align | 文字水平对齐方式，默认自动。'left'，'center'，'right'        |
|  vertical_align  | 文字垂直对齐方式，默认自动。'top'，'middle'，'bottom'        |



###### 文字样式配置项

opts.TextStyleOpts() --文字样式配置项

name_textstyle_opts=opts.TextStyleOpts() ---坐标轴的文字样式配置项

|       参数       | 说明                 |
| :--------------: | :------------------- |
|      color       | 表示文字颜色         |
|    font_size     | 表示文字的字体大小   |
|      align       | 表示文字水平对齐方式 |
|  vertical_align  | 表示文字垂直对齐方式 |
|   line_height    | 表示行高             |
|    font_style    | 表示文字字体风格     |
|   font_weight    | 表示主标题字体的粗细 |
| background_color | 表示文字块背景色     |
|   border_color   | 表示文字块边框颜色   |
|   border_width   | 表示文字块边框宽度   |

###### 线样式配置项

opts.LineStyleOpts()-----线样式配置项

折线图可以直接在`add_yaxis`直接使用`linestyle_opts=opts.LineStyleOpts()`

|  参数   | 说明                                                         |
| :-----: | :----------------------------------------------------------- |
| is_show | 是否显示                                                     |
|  width  | 线宽                                                         |
| opacity | 图形透明度。支持从 0 到 1 的数字，为 0 时不绘制该图形        |
|  curve  | 线的弯曲度，0 表示完全不弯曲                                 |
|  type_  | 线的类型。'solid', 'dashed', 'dotted'（“实线”、“虚线”、“点划线”） |

###### 标记点数据项

opts.MarkPointItem() --- 标记点数据项

|      参数      | 说明                                                         |
| :------------: | :----------------------------------------------------------- |
|      name      | 标注名称                                                     |
|  symbol_size   | 标记的大小，也可以用数组分开表示宽和高                       |
|     type_      | 特殊的标注类型，用于标注最大值最小值等，'min' , 'max','average' 平均值 |
|     coord      | 标注的坐标。坐标格式视系列的坐标系而定,也可以是极坐标系上的 radius, angle |
|     symbol     | 标记的图形:circle, rect, roundRect, triangle,圆形、矩形、圆形矩形、三角形 |
| itemstyle_opts | 标记点样式配置项                                             |



###### 分割线配置项

SplitLineOpts()

| 参数           | 描述                        |
| -------------- | --------------------------- |
| is_show        | 是否显示分割    默认为False |
| linestyle_opts | 线风格配置项                |



### 组合组件(Grid)

```py
bar_pie =(Grid(init_opts=opts.InitOpts(width='950px', height='600px'))
              .add(bar, grid_opts=opts.GridOpts(pos_right='50%'))
              .add(pie, grid_opts=opts.GridOpts(pos_left='70%'))).render_embed()
    return render(request,'bar_pie.html',{'bar_pie':bar_pie})
```



### HTML篇

将图表移动到HTML页面的合适位置

先用`div`将图表包裹起来，定义一个id

在`head`标签下创建一个`style`属性

 /#+ `id名`{}

| 参数     | 描述                       |
| -------- | -------------------------- |
| position | 位置；  'absolute'绝对位置 |
| top      | 距离上面                   |
| bottom   | 距离下面                   |
| right    | 距离右边                   |
| left     | 距离左边                   |

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>柱状折线图</title>
    <style>
        #bar_line{
    position:absolute;
    top:450px;
    left:800px;
    }
    </style>
</head>
<body>
    <div id="bar_line">
        {{bar_line|safe}}
    </div>
</body>
</html>
```



#### Bar(柱状图/条形图)

Bar.add() 方法签名

```py
add(name, x_axis, y_axis,
    is_stack=False,bar_width='',
    bar_category_gap='20%', **kwargs)
```

- **name** -> str
  图例名称

- **x_axis** -> list
  x 坐标轴数据

- **y_axis** -> list
  y 坐标轴数据

- **is_stack** -> bool
  数据堆叠，同个类目轴上系列配置相同的 stack 值可以堆叠放置

- **bar_width** -> int/str

  柱子的宽度

- **bar_category_gap** -> int/str
  类目轴的柱状距离，当设置为 0 时柱状是紧挨着（直方图类型），默认为 '20%'
  
- color  ->  Optional[str] = None
  系列label颜色

-  is_show_background: bool = False
   是否显示柱条的背景色。通过 backgroundStyle 配置背景样式

- gap: Optional[str] = "30%"
  不同系列的柱间距离，为百分比（如 '30%'，表示柱子宽度的 30%）。 
  如果想要两个系列的柱子重叠，可以设置 gap 为 '-100%'。这在用柱子做背景的时候有用

  | 参数           | 描述             |
  | -------------- | ---------------- |
  | markpoint_opts | 标签配置项       |
  | markpoint_opts | 标记点配置项     |
  | markline_opts  | 标记线配置项     |
  | tooltip_opts   | 提示框组件配置项 |
  | itemstyle_opts | 图元样式配置项   |



#### Line(折线图/面积图)

add_yaxis()

| 参数           | 描述                                                         |
| -------------- | ------------------------------------------------------------ |
| series_name    | 系列名称                                                     |
| y_axis         | 系列数据                                                     |
| color          | 系列 label 颜色                                              |
| symbol         | 标记的图形'circle', 'rect', 'roundRect', 'triangle',     # 'diamond', 'pin', 'arrow', 'none' |
| symbol_size    | 标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，    # 例如 [20, 10] 表示标记宽为 20，高为 10。 |
| stack          | 数据堆叠，同个类目轴上系列配置相同的　stack　值可以堆叠放置  |
| is_smooth      | 是否平滑曲线                                                 |
| is_step        | 是否显示成阶梯图                                             |
|                |                                                              |
| markpoint_opts | 标记点配置项                                                 |
| markline_opts  | 标记线配置项                                                 |
| tooltip_opts   | 提示框组件配置项                                             |
| label_opts     | 标签配置项                                                   |
| linestyle_opts | 线样式配置项                                                 |
| areastyle_opts | 填充区域配置项                                               |
| itemstyle_opts | 图元样式配置项                                               |
|                |                                                              |
|                |                                                              |



#### 饼图(pie)

add()

| 参数                 | 描述                                                         |
| -------------------- | ------------------------------------------------------------ |
| series_name          | 系列名称                                                     |
| data_pair            | 系列数据项                                                   |
| selected_offset      | 选中扇区的偏移距离                                           |
| radius               | 饼图的半径，数组的第一项是内半径，第二项是外半径             |
| center               | 饼图的中心（圆心）坐标，数组的第一项是横坐标，第二项是纵坐标 |
| is_clockwise         | 饼图的扇区是否是顺时针排布                                   |
| start_angle          | 起始角度，支持范围 [0，360]                                  |
| min_angle            | 最小的扇区角度（0 ~ 360），用于防止某个值过小导致扇区太小影响交互。 |
| min_show_label_angle | 小于这个角度（0 ~ 360）的扇区，不显示标签                    |
| percent_precision    | 饼图百分比数值的精度，默认保留小数点后两位                   |
| label_opts           | 标签配置项                                                   |
| tooltip_opts         | 提示框组件配置项                                             |
| itemstyle_opts       | 图元样式配置项                                               |
| color                | \# 从调色盘 option.color 中取色的策略，可取值为：            |
|                      | # 'series'：按照系列分配调色盘中的颜色，同一系列中的所有数据都是用相同的颜色； |
|                      | # 'data'：按照数据项分配调色盘中的颜色，每个数据项都使用不同的颜色。    color_by: types.Optional[str] = "data", |

饼图数据项  pieltem（）

| 参数           | 描述             |
| -------------- | ---------------- |
| name           | 数据项名称       |
| value          | 数据值           |
| label_opts     | 标签配置项       |
| itemstyle_opts | 图元样式配置项   |
| tooltip_opts   | 提示框组件配置项 |



#### 散点图(Scatter)

add_yaxis()

| 参数           | 描述                                                         |
| -------------- | ------------------------------------------------------------ |
| series_name    | 系列名称                                                     |
| xaxis_index    | 使用的 x 轴的 index，在单个图表实例中存在多个 x 轴的时候有用 |
| yaxis_index    | 使用的 y 轴的 index，在单个图表实例中存在多个 y 轴的时候有用 |
| color          | 系列 label 颜色                                              |
| symbol         | 标记的图形。'circle', 'rect', 'roundRect', 'triangle',     # 'diamond', 'pin', 'arrow', 'none' |
| symbol_size    | 记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高 |
| symbol_rotate  | 标记的旋转角度                                               |
|                |                                                              |
| label_opts     | 标签配置项                                                   |
| markpoint_opts | 标记点配置项                                                 |
| markline_opts  | 标记线配置项                                                 |
| markarea_opts  | 图表标域，常用于标记图表中某个范围的数据                     |
| tooltip_opts   | 提示框组件配置项                                             |
| itemstyle_opts | 图元样式配置项                                               |



#### 热力图(HeatMap)

add_yaxis()

| 参数           | 描述             |
| -------------- | ---------------- |
| series_name    | 系列名称         |
| yaxis_data     | Y 坐标轴数据     |
| value          | 系列数据项       |
|                |                  |
| label_opts     | 标签配置项       |
| markpoint_opts | 标记点配置项     |
| markline_opts  | 标记线配置项     |
| tooltip_opts   | 提示框组件配置项 |
| itemstyle_opts | 图元样式配置项   |
|                |                  |

HeatMapItem    热力图数据项

| 参数           | 描述             |
| -------------- | ---------------- |
| name           | 数据项名称       |
| value          | 数据项的值       |
| itemstyle_opts | 图元样式配置项   |
| tooltip_opts   | 提示框组件配置项 |



#### 雷达图(Radar)

add_schema()

| 参数            | 说明                                                         |
| --------------- | ------------------------------------------------------------ |
| schema          | 雷达指示器配置项列表                                         |
| shape           | 雷达图绘制类型，可选 'polygon'(多边形) 和 'circle'(圆形)     |
| center          | 雷达的中心（圆心）坐标，数组的第一项是横坐标，第二项是纵坐标 |
| textstyle_opts  | 文字样式配置项                                               |
| splitline_opt   | 分割线配置项                                                 |
| splitarea_opt   | 分隔区域配置项                                               |
| axisline_opt    | 坐标轴轴线配置项                                             |
| radiusaxis_opts | 极坐标系的径向轴                                             |
| angleaxis_opts  | 极坐标系的角度轴                                             |
| polar_opts      | 极坐标系配置                                                 |

RadarIndicatorItem  雷达指示器配置

| 参数  | 说明           |
| ----- | -------------- |
| name  | 指示器名称     |
| min_  | 指示器的最小值 |
| max_  | 指示器的最大值 |
| color | 标签特定的颜色 |

add()

| 参数           | 说明                   |
| -------------- | ---------------------- |
| series_name    | 系列名称               |
| data           | 系列数据项             |
| is_selected    | 是否选中图例，默认True |
| color          | 系列 label 颜色        |
| label_opts     | 标签配置项             |
| linestyle_opts | 线样式配置项           |
| areastyle_opts | 区域填充样式配置项     |
| tooltip_opts   | 提示框组件配置项       |



#### 词云图(Worclou)

add()

| 参数                      | 描述                                                         |
| ------------------------- | ------------------------------------------------------------ |
| series_name               | 系列名称                                                     |
| data_pair                 | 系列数据项                                                   |
| shape                     | 词云图轮廓，有 'circle', 'cardioid', 'diamond', 'triangle-forward', 'triangle', 'pentagon', 'star' |
| word_gap                  | 单词间隔                                                     |
| word_size_range           | 单词字体大小范围                                             |
| rotate_step               | 旋转单词角度                                                 |
| pos_left/right/top/bottom | 距离左/右/上/下侧的距离                                      |
| height                    | 词云图的高度                                                 |
| is_draw_out_of_bound      | 允许词云图的数据展示在画布范围之外                           |
|                           |                                                              |
| tooltip_opts              | 提示框组件配置项                                             |
| textstyle_opts            | 词云图文字的配置                                             |
| emphasis_shadow_blur      | 词云图文字阴影的范围                                         |
| emphasis_shadow_color     | 词云图文字阴影的颜色                                         |



#### 地图(Map)

add()

| 参数                    | 描述                              |
| ----------------------- | --------------------------------- |
| series_name             | 系列名称                          |
| data_pair               | 数据项 (坐标点名称，坐标点值)     |
| maptype                 | 地图类型  maptype: str = "china", |
| min_scale_limit         | 最小的缩放值                      |
| max_scale_limit         | 最大的缩放值                      |
| symbol                  | 标记图形形状                      |
| layout_size             | 地图的大小                        |
| label_opts              | 标签配置项                        |
| tooltip_opts            | 提示框组件配置项                  |
| 图元样式配置项          | 图元样式配置项                    |
| emphasis_label_opts     | 高亮标签配置项                    |
| emphasis_itemstyle_opts | 高亮图元样式配置项                |

### 效果篇

#### x/y轴的网格线(分割线)

在全局配置中设置，坐标轴配置项中使用splitline_opts

```py
.set_global_opts(
xaxis_opts=opts.AxisOpts(splitline_opts=opts.SplitLineOpts(is_show=True))#显示x轴分割线

yaxis_opts=opts.AxisOpts(splitline_opts=opts.SplitLineOpts(is_show=True))#显示y轴分割线
)
```

