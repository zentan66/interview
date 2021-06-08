### 简单

#### 1. MVC 和 MVVM 区别

##### MVC

MVC全称是Model View Controller，是模型-视图-控制器的缩写，一种软件设计的典范

- Model：应用程序中用于处理应用程序数据逻辑的部分
- View：应用程序中处理数据显示的部分
- Controller：应用程序中处理用户交互的部分

MVC的核心就是通过controller将Model的数据显示在View中

##### MVVM

- ViewModel：数据双向绑定，将模型转化成视图（将后端传递的数据转化成所看到的页面），另一方面将视图转化成模型，即将所看到的页面转化成后端的数据

MVVM比MVC精简很多，不仅简化了业务与界面的依赖，还解决了数据频繁更新的问题，不用再用选择器操作DOM

##### MVVM

#### 2. 为什么data是一个函数

组件中的data是以函数返回值形式定义的，每复用一次组件，就会返回一份新的data，类似于给每个组件实例创建一个私有的数据空间，让各个组件实例维护各自的数据，而写成对象形式，就会使得所有组件实例共用一份data

#### 3.vue组件通信方式

- props+emit
- $parent、$children获取当前组件的父组件或子组件
- $attrs和$listeners
- $refs
- provide/inject
- Event Bus
- Vuex

#### 4.vue的生命周期，一般在哪一步发请求

**beforeCreate**在实例初始化之后，数据观测和event/watcher事件配置之前被调用。当前阶段的data、methods、computed以及watch上的数据和方法都不能访问

**created**实例已经创建完成之后被调用，例如data、数据和方法，watch/event事件回调都已配置，但是没有`$el`，如果非要与DOM进行交互，可以通过`vm.$nextTick`访问DOM

**beforeMount**在挂载开始之前被调用：相关的render函数首次被调用

**mounted**在挂载完成后发成，在当前阶段，真实的DOM挂载完毕，数据完成双向数据绑定，可以访问到DOM节点

#### 5.怎样理解vue单向数据流

```markdown
数据从父组件传递到子组件，且子组件不允许修改从父组件传递到子组件的数据
```

#### 虚拟DOM的优缺点

```markdown
优点：
1.保证性能下限（具有普适性）
2. 无需手动操作DOM
3. 跨平台
缺点：
1.无法进行极致优化
2. 首次会比innerHTML插入慢
```

#### 7.v-for为什么要加key

```markdown
如果不使用key，vue会使用一种最大限度减少动态元素并且尽可能的尝试就地修改/复用相同类型元素的算法
key是为vue中vnode的唯一标记，通过这个key，我们的diff操作可以更加快速、准确
```

#### 8.Vue 的响应式对数组是如何处理的？

#### 9.Object为什么可以自动派发更新



