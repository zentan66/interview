### margin合并

#### 定义

> 块级元素的上外边距与下外边距有时会合并为单个外边距的现象

#### 要求

- `块级元素`，不包括浮动和绝对定位的元素
- `只发生在垂直方向`，严格来讲，应该是和当前文档流方向相垂直的方向上

#### 类型

##### 兄弟元素合并

##### 父子元素合并

**阻止合并的方式**

阻止`margin-top`合并：

- 父元素设置为`BFC`
- 父元素设置`border-top`
- 父元素设置`padding-top`
- 父元素和第一个子元素之间添加内联元素分隔

阻止`margin-bottom`合并：

- 父元素设置为`BFC`
- 父元素设置`border-bottom`
- 父元素设置`padding-bottom`
- 父元素和最后一个子元素之间添加内联元素分隔
- 父元素设置`height`、`min-height`或`max-height`

##### 空元素合并

举个栗子：

```css
.father { overflow: hidden; }
.son { margin: 1em 0; }
<body>
  <div class="father">
    <div class="son"></div>
  </div>
</body>
```

显示效果是父级元素的高度仅仅是1em，因为子元素的`margin-top`和`margin-bottom`发生了合并

**阻止空元素合并的方式**

- 设置垂直方向的border
- 设置垂直方向的padding
- 里面添加内联元素
- 设置height或min-height

### margin: auto

#### 巧用auto值

栗子：

```css
.father { width: 300px; }
.son { width: 200px; height: 30px; margin-left: auto; margin-right: 80px; }
```

上述栗子的效果就是左边会有20px的边距，相当于把子元素向右移动了20px

如果将margin-right去除，又会显示成什么效果呢？

大概就是右对齐了吧，这样一来就可以不使用`float: right`就能实现块级元素的右对齐效果了

#### 那么为什么auto不能上下居中？

原因就是触发margin：auto计算有一个前提条件，就是width或height为auto时，元素是具有对应方向的自动填充特性的。

能有什么办法用auto实现上下居中么？答案肯定是有的

**1.更改文档流方向**

```css
.father {
  height: 200px;
  writing-mode: vertical-lr;
}
.son {
  height: 100px;
  margin: auto;
}
```

这样的方法是将文档流从水平更改到了垂直，造成的结果就是水平方向没办法进行居中，并且得设置宽度

**2.绝对定位元素+margin：auto**

```css
.father {
  position: relative;
  height: 200px;
}
.son {
  position: absolute;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
  width: 200px;
  height: 100px;
  margin: auto;
}
```

通过绝对定位使子元素铺满父级元素区域，而后设置子元素宽高，这样就会空出一大片区域，这片区域就能使用margin：auto让子元素垂直水平居中

### margin无效

- display为inline的非替换元素的垂直margin无效，内联替换元素垂直margin有效，且没有margin合并
- 表格中的tr和td元素或者diaplay设置为table-cell或table-row元素的margin都是无效的
- margin合并的时候，更改margin值没有效果
- 绝对定位元素的非定位方向的margin值“无效”

