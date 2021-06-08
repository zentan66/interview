### 定义

> 页面中一个渲染区域，有自己的一套渲染规则，决定其子元素如何定位，以及和其他兄弟元素的关系和作用

### 特性

- 内部box会在垂直方向上，一个接一个地放置
- box垂直方向的距离由margin决定，同一个BFC下的两个相邻box的margin会发生折叠
- 每一个元素的margin box的左边，与包含块border box的左边相接触，即便浮动元素也是如此
- BFC区域不会与float box叠加
- 计算BFC的高度时，浮动子元素也参与计算
- 文字层不会被浮动层覆盖，环绕于周围

### 如何产生

- float除了none以外的值
- overflow除了visible以外的值
- display(table-cell，table-caption，inline-block，flex，inline-flex)
- position（absolute，fixed)

### 作用

- 解决上外边距重叠
- 解决浮动引起的高度塌陷
- 解决文字环绕图片