### 百分比
父元素设置`line-height`，就固定了`line-height`，子元素将继承这个固定的值

```html
<style>
.parent {
  font-size: 14px;
  line-height: 150%;
}
.child {
  font-size: 26px;
}
</style>
<body>
<div class="parent">
  <div class="child"></div>
</div>
</body>
```
在`child`中的元素的行高继承`parent`的，因此数值是21px

### 数值
子元素将继承`line-height`的倍数，而不是固定数值
```html
<style>
.parent {
  font-size: 14px;
  line-height: 1.5;
}
.child {
  font-size: 26px;
}
</style>
<body>
<div class="parent">
  <div class="child"></div>
</div>
</body>
```
在`child`中的元素的行高1.5倍，因此数值是39px