1. p标签文本没法设置高度，如何让前n个字符变高
2. 盒模型
3. BFC（触发条件，规则，应用）
4. 清除浮动的方式，以及原理

## 预编译

#### scss

1. 如何复用变量
2. @和%有什么区别



## QA

1. 介绍下标准的CSS的盒子模型？低版本IE的盒子模型有什么不同的？

```
盒子模型有两种：IE盒模型、W3C标准盒模型
盒模型包括：内容（content）、填充（padding）、边界（margin）和边框（border）
两种盒模型的区别：
- IE盒模型：属性witth、height包含content、border和padding
- 标准盒模型：属性width、height只包含content
可以通过属性box-sizing控制盒模型，默认content-box，IE盒模型是border-box
```

2. `::before`和`:after`中双冒号和单冒号的区别？解释这两个伪元素的作用

```
单冒号（：）用于CSS伪类，双冒号（::)用于CSS伪元素
CSS3中使用单冒号来表示伪类，用双冒号来标识伪元素
伪类一般匹配的是元素的一些特殊状态，如hover、link等，而伪元素一般匹配的特殊的位置，比如after、before等。
```

3. 伪类与伪元素的区别

```
伪类用于当已有的元素处于某个状态时，为其添加对应的样式
伪元素用于创建一些不在文档书中的元素，并为其添加样式
```

4. CSS优先级算法如何计算

```
略
```

5. 如何居中div

```
常用居中方法：
1. margin: 0 auto;
2. 利用绝对定位，设置四个方向值都为0，margin: auto;
3. 绝对定位，top和left设置为50%，margin负值
4. 绝对定位，top和left设置为50%，translate
5. flex布局
```

6. 介绍下CSS3下的Flexbox

```
容器属性：
flex-direction 决定主轴方向
flex-wrap 如果一条轴线排不下，如何换行
flex-flow flex-direction和flex-wrap的简写形式
justify-content 项目在主轴上对齐的方式
align-items 项目在交叉轴上如何对齐
align-content 多根轴线的对齐方式

项目属性：
order 定义项目的排序顺序

```

