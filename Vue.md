### 数据双向绑定

### computed原理

computed是定义在vm上的一个特殊的getter方法

计算属性的结果会被缓存，且只有在计算属性所依赖的响应式属性或者说计算属性的返回值发生变化时才会重新计算

通过Watcher的dirty属性来分辨，当dirty属性为true时，说明需要重新计算；当dirty属性为false时，说明计算属性的值并没有改

计算属性会通过Watcher来观察它所用到的所有属性的变化，当这些属性发生变化时，计算属性会将自身的Watcher的dirty属性设置为true，说明自身的返回值变了

### watch原理

#### 源码

```javascript
// state.js
function initState(vm) {
  const opts = vm.$options
  if (opts.watch && opts.watch !== nativeWatch) {
    initWatch(vm, opts.watch)
  }
}
```

最终调用的是：

```javascript
vm.$watch(expOrFn, handler, options)
```

将需要观察的值都调用该组件的watch进行观察

### 生命周期



### 组件通信



### dom diff



### vuex



### vue-router

