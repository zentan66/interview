### 问题集

- 为什么border-width不支持百分比？

#### 某一方向不添加border

```css
div {
  border: 1px solid;
  border-bottom: none;
}
```

上述方式的渲染性能最高

#### 布局

##### 等高布局

```css
.box {
  border-left: 150px solid #333;
  background-color: #f0f3f9;
}
.box > nav {
  width: 150px;
  margin-left: -150px;
  float: left;
}
.box > section {
  overflow: hidden;
}
```

### 特效

##### 三角形

```css
div {
  width: 0;
  border: 10px solid;
  border-color: #f30 transparent transparent;
}
```

##### 不同形状的三角形

```css
div {
  width: 0;
  border-width: 10px 20px;
  border-style: solid;
  border-color: #f30 transparent transparent;
}
```

##### 直角三角形

```css
div {
  width: 0;
  border-width: 10px 20px;
  border-style: solid;
  border-color: #f30 #f30 transparent transparent;
}
```

##### 四色矩形

```css
div {
  width: 10px;
  height: 10px;
  border: 10px solid;
  border-color: #f30 #00f #396 #0f0;
}
```

##### 矩形

```css
div {
  width: 10px;
  height: 10px;
  border: 10px solid;
  border-color: #f30 transparent transparent;
}
```

