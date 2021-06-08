



#### preserveAspectRatio

> 指定对齐方式

模型：

```xml
preserveAspectRatio="alignment [meet|slice]"
```

默认值：`xMidYMid meet`

#### 颜色

- 基本颜色关键字：aqua、black、blue、fuchsia

- 6位十六进制数字

- 3位十六进制数字

- rgb

- `currentColor`

  表示当前元素应用的CSS属性的color值

#### 属性列表

- stroke

- stroke-width

- stroke-opacity

- stroke-dasharray

- stroke-linecap

  线帽[butt/round/square]

- stroke-linejoin

  线条交叉时的效果[miter/round/bevel]

- fill

- fill-opacity

- fill-rule

  判断某个点是否在图形内部[nonzero/evenodd]

#### 样式表

内联样式几乎总是比内部或外部样式表渲染得更快，这是因为样式表和类增加了渲染时的查询和解析时间

##### 优先级

内联样式 > 内部/外部样式表 > 表现属性 > 继承样式

### 标签

#### \<use\>元素

> 用于复用组合的部分内容

实例：

```xml-dtd
<g id="house">
	<rect x="0" y="0" width="100" height="100"></rect>
</g>
<use xlink:href="#house"></use>
```



#### \<symbol\>元素

>  一种组合元素的方式，永远不会显示

#### \<image\>元素

#### \<marker\>元素

向路径上添加标记

```xml-dtd
<defs>
	<marker id="mCircle" markerWidth="10" markerHeight="10" refX="5" refY="5">
  	<circle cx="5" cy="5" r="4" style="fill:none;stroke:black;"></circle>
  </marker>
</defs>
<path d="M10 20 100 20 A 20 30 0 0 1 120 50 L 120 110" style="marker-start: url(#mCircle);fill:none;stroke:black;" />
```

应用标记的几种属性：

- marker-start
- marker-mid
- marker-end
- marker

##### 适用范围

\<polygon\>、<polyline\>或者\<line\>元素以及\<path\>

##### orient

标记的方向需要在`marker`上设置`orient`的值为auto，标记会自动旋转匹配路径的方向

##### markderUnit

- `strokeWidth`：标记的坐标系会被设定为单位等于笔画宽度
- `userSpaceOnUse`：标记的坐标系统会被假定位和引用该标记的对象的坐标系统一样

### 路径

#### 基本名词

**d**：数据

**M**：moveto

**L**：lineto

**Z**：closepath 用于关闭路径

**A**：圆弧命令

**Q**：曲线（x1,y1,x,y）

**T**：二次曲线(x, y)

**C**：三次曲线（起点控制点，终点控制点，端点）

**S**：多条连接在一起的三次曲线(x2, y2, x, y)

**m、l、a**：相对于当前画笔的位置的定位

#### 介绍

每个路径都必须以moveto命令开始

##### 快捷路径

**H**：水平绝对路径

```xml
<path d="M 10 10 H 30"></path>
```

从点（10,10）触发，绘制一条横向长度20的线条

**h**：水平相对路径

```xml
<path d="M 10 10 h 20"></path>
```

等价于上一个例子的效果

**V**：垂直绝对路径

**v**：垂直相对路径

##### 路径快捷写法

- 可以在L或者l后面放多组坐标

```xml
<g style="stroke: black;fill: none;">
	<path d="M 30 30 L 55 5 L 80 30 L 55 55 Z"></path>
	<path d="M 30 30 L 55 5 80 30 55 55 Z"></path>
	<path d="M 30 30 55 5 80 30 55 55 Z"></path>
</g>
```

- 所有不必要的空白都可以消除。命令字母后面不需要空白，数字和命令之间不需要空白，正数负数之间不需要空白

```xml
<path d="M30 30 55 5 80 30 55 55Z"/>
```

#### 椭圆弧

#### 参数

- 点所在椭圆的x，y半径
- 椭圆的x轴旋转角度
- 圆弧角度小于180=>0，圆弧角度大于等于180=>1
- 负角度绘制=>0，正角度绘制=>1
- 终点x，y坐标

### 图案

图案的创建需要使用`<pattern>`标签

#### 属性列表

**patternUnits**

每个图案填充对象的一定百分比

- objectBoundingBox
- userSpaceOnUse

**patternContentUnits**

- objectBoundingBox

#### 渐变

- 线性渐变`linearGradient`

```xml
<svg>
  <def>
    <linearGradient>
      <stop offset="percent" stop-color="" stop-opacity="" />
    </linearGradient>
  </def>
</svg>
```

- 径向渐变`radialGradient`

```xml
<svg>
  <defs>
  	<radialGradient id="three_stops" cx="0%" cy="0%" fx="50%" fy="50%" r="141%">
      <stop offset="" stop-color=""></stop>  
    </radialGradient>  
  </defs>
</svg>
```

##### 属性

- `gradientTransform`
- `patternTransform`

#### 裁剪路径

### 动画

#### 基础配置属性

- attributeName 动画中持续改变的值
- attributeType 上述属性是XML属性或者CSS属性
- 属性的起始（from）与结束（to）值
- begin、dur 动画的开始时间与持续时间
- fill 动画结束时的动作 [freeze/remove]
- repeatCount 重复几次
- repeatDur 持续多久

#### set标签

设置初始不显示的项

```xml
<text text-anchor="middle" x="60" y="60" style="visibility:hidden">
  <set attributeName="visibility" attributeType="CSS" to="visible" begin="4.5s" dur="1s" fill="freeze"></set>
</text>
```

#### animateTransform

animate元素不适用于旋转、平移、缩放或倾斜变换

```xml
<g transform="translate(100,60)">
  <rect x="-10" y="-10" width="20" height="20" style="fill:#ff9;stroke:black;">
    <animateTransform attributeType="XML" attributeName="transform" type="scale" from="1" to="4 2" begin="0s" dur="4s" fill="freeze"></animateTransform>  
  </rect>
</g>
```

#### animateMotion

定义元素的线性运动

```xml
<animateMotion from="0,0" to="60,30" dur="4s" fill="freeze"></animateMotion>
```

如果是沿着路径运动，则使用path替换from和to

##### 属性

- rotate [number/'auto'] 动画元素的旋转角度
- keyTimes [\<number\>Array]
- keyPoints [\<number\>Array]