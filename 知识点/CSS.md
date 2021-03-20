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

7. 三角形的原理

```css
#demo {
  width: 0;
  height: 0;
  border-width: 20px;
  border-style: solid;
  border-color: transparent transparent red transparent;
}
```

8. 多列等高如何实现

```css
/** 1. 利用margin-bottom和padding-bottom实现 */
.Article {
  overflow: hidden;
}

.Article>li {
  float: left;
  margin: 0 10px -9999px 0;
  padding-bottom: 9999px;
  background: #4577dc;
  width: 200px;
  color: #fff;
}
/** 2. 模仿table布局 */
.Article {
  display: table;
  width: 100%;
  table-layout: fixed;
}

.Article>li {
  display: table-cell;
  width: 200px;
  border-left: solid 5px currentColor;
  border-right: solid 5px currentColor;
  color: #fff;
  background: #4577dc;
}
/** 3. 模仿table布局 */
/** 4. grid布局 */
.article {
  display: grid;
  grid-auto-flow: column;
  grid-gap: 20px;
}
```

9. 常见浏览器兼容性有哪些？原因？解决办法？常用hack技巧

```
- png24位图片在IE6浏览器上出现背景
解决办法：换成PNG8

- 浏览器默认的margin和padding不同
解决办法：加一个全局 * {margin: 0;padding: 0;}

- IE双边距bug，在IE6下对元素设置了浮动，同时又设置了margin-left或margin-right，margin值会加倍
解决办法：# { float: left;width: 10px;margin: 0 0 0 10px;}
```

10. li和li之间有看不见的空白间隔是什么原因引起的？解决办法

```
浏览器会把inline元素间的空白字符（空格、换行、Tab等）渲染成一个空格。而为了美观。我们通常是一个<li>放在一行，
这导致<li>换行后产生换行字符，它变成一个空格，占用了一个字符的宽度。

解决办法：
1. 设置float:left;
2. 将所有li写在同一行
3. 设置ul的font-size:0;，li的font-size为需要的字符大小
4. ul设置letter-spacing: -8px;
```

11. `width:auto;`和`width:100%`的区别

```
一般而言

width:100%会使元素box的宽度等于父元素的contentbox的宽度。

width:auto会使元素撑满整个父元素，margin、border、padding、content区域会自动分配水平空间。
```

12. 简单介绍下图片base64编码的优缺点

```
base64编码是一种图片处理格式，通过特定的算法将图片编码成一长串字符串，在页面上显示的时候，可以用该字符串来代替图片的url属性
优点：
1. 减少图片的HTTP请求
缺点：
1.图片过大，会导致文件体积增大，影响文件的加载速度
2.无法缓存
3.兼容性问题
```

13. 为什么需要清除浮动？清除浮动的方式

```
当包含框的高度小于浮动框的时候，就会出现“高度塌陷”
清除浮动的方式：
1. clear属性
2. 使用BFC块级格式化上下文来清除浮动
```

14. clear属性清除浮动的原理

```
略
```

15. `zoom:1`清除浮动的原理

```
清除浮动，触发hasLayout
zoom属性是IE浏览器的专有属性，可以设置或检索对象的缩放比例，解决ie下比较奇葩的bug
```

16. CSS优化、提高性能的方法

```
加载性能：
1. css压缩
2. 减少@import而使用link
选择器性能：
1. 尽量减少用标签选择，而用class
2. 避免使用通配规则
3. 尽量少的去使用后代选择器，降低选择器的权重值
4. 如果规则拥有ID选择器作为其关键选择器，则不要为规则增加标签
渲染性能：
1. 慎重使用高性能属性
2. 尽量减少页面重绘、重排
3. 去除空规则
4. 属性值为0时，不加单位
5. 属性值为0.xxx，可以省略小数点之前的0
6. 标准化浏览器前缀
7. 不使用@import
8. 选择器优化，避免层级过深
9. css雪碧图
10. 正确使用display属性
11. 不滥用web字体
可维护性，健壮性：
1. 将具有相同属性的样式抽出来，整合并通过class在页面中进行使用
2. 样式与内容分离，将css代码定义到外部css中
```

17. 浏览器是怎样解析CSS选择器的

```
样式系统从关键选择器开始匹配，然后左移查找规则选择器的祖先元素。只要选择器的子树一直在工作，样式系统就会持续左移，直
到和规则匹配，或者是因为不匹配而放弃该规则。

试想一下，如果采用从左至右的方式读取CSS规则，那么大多数规则读到最后（最右）才会发现是不匹配的，这样做会费时耗能，
最后有很多都是无用的；而如果采取从右向左的方式，那么只要发现最右边选择器不匹配，就可以直接舍弃了，避免了许多无效匹配。
```

18. 为什么不建议使用通配符初始化css样式

```
//
```

