### vue

1. 项目优化
2. computed和watch区别
3. MVVM如何实现
4. diff算法理解
5. 单页面多页面区别
6. 生命周期
7. mount阶段做什么
8. 项目中有多个环境怎么处理
9. v-once是如何实现的
10. vue项目比起传统项目有什么优势
11. vue如何实现自定义指令
12. vue项目中状态判断如何处理，比如判断登录状态
13. vue单向数据流
14. vue生命周期，哪个阶段可以操作DOM
15. 讲一下v-slot：命名插槽+作用域插槽
16. vue.$set的原理
17. vue如何做权限校验
18. vue如何收集依赖的

#### 组件中写name选项有什么作用

1. 项目使用 keep-alive 时，可搭配组件 name 进行缓存过滤
2. DOM 做递归组件时需要调用自身 name
3. vue-devtools 调试工具里显示的组见名称是由vue中组件name决定的

#### keep-alive使用

#### Vue 为什么要用 vm.$set() 解决对象新增属性不能响应的问题 ？

1. Vue使用了Object.defineProperty实现双向数据绑定
2. 在初始化实例时对属性执行 getter/setter 转化
3. 属性必须在data对象上存在才能让Vue将它转换为响应式的（这也就造成了Vue无法检测到对象属性的添加或删除）

#### 既然 Vue 通过数据劫持可以精准探测数据在具体dom上的变化,为什么还需要虚拟 DOM diff 呢?

React的变化时通过setState API显式更新的，然后React会进行一层层的VIrtual Dom Diff操作找出差异，然后patch到DOM上。React从一开始就不知道到底是哪发生了变化，只是知道「有变化了」，然后再进行比较暴力的Diff操作查找「哪发生变化了」

Vue在程序初始化的时候就会对数据data进行依赖的收集，一但数据发生变化，响应式系统就会立刻得知。但是一个绑定一个数据就需要一个Watcher，如果绑定细粒度过高就会产生很多Watcher，这会带来内衣以及依赖追踪的开销，而细粒度过低会无法精准侦测变化，因此Vue的设计师选择中等细粒度的方案，在组件级进行push侦测的方式，通常我们会第一时间侦测到发生变化的组件，然后在组件内部进行Virtual Dom Diff获取更加具体的差异

#### 从页面创建和页面更新角度来说一下vue的虚拟dom和diff算法



#### 说一下构建虚拟dom树时，用了什么算法



### vuex

1. vuex包括哪些内容

### vue-router

1. vue-router钩子介绍
2. 懒加载实现
3. location.href和vue-router跳转有什么区别
4. 一个新的路由，怎么知道下载对应的文件？

## QA

vue和react用起来有什么区别？

```
相同之处：
1.组件化 2.都是virtual dom + diff
不同：
1. 模板语法
2. 监听数据变化原理不同
vue通过getter、setter劫持通知数据变化，响应式数据，直接赋值
react通过比较引用的方式，不可变数据，setState方法
```

vue双向数据绑定原理，数组的更新

```

```

组件间通信的方式？vuex实现原理？state改变，如何促使组件改变？

```
//
```

vue3的类似hooks的原理是怎么样的？

