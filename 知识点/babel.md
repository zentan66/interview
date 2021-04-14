

### @babel/preset-env

```js
module.exports = {
  presets: [
    ["@babel/env", {
      loose: true,
      modules: false,
      useBuiltIns: 'usage',
      corejs: 3
    }]
  ]
}
```

#### useBuiltIns属性

前提条件：引入`@babel/polyfill`

- `false`：不对`polyfill`做任何操作
- `entry`：根据`target`中浏览器版本的支持，对`polyfill`拆分引入
- `usage`：检测代码中`ES6/7/8`等的使用情况，仅仅加载代码中用到的`polyfills`

### @babel/polyfill

**polyfill**的中文意思是垫片，顾名思义就是垫平不同浏览器或者不同环境下的差异，让新的内置函数、实例方法等在低版本浏览器中也可以使用。

### @babel/plugin-transform-runtime

作用

- 解决全局污染
- 代码复用