

## React

### 基础内容

1. 生命周期，每个阶段做什么
2. React性能优化
3. React状态逻辑复用问题
4. React Fiber节点



#### setState什么时候是同步，什么时候是异步

```
由react控制的事件处理程序以及生命周期函数调用都不会同步更新state
react控制之外的事件中调用时同步更新，比如原生js绑定的事件，setTimeout/setInterval
```

#### 请问React调用机制一共对任务设置了几种优先级别？每种优先级都代表的具体含义是什么？在你开发过程中如果遇到影响主UI渲染卡顿的任务，你又是如何利用这些优先级的？

```javascript
// 初始化和重置root和占位用的
export const NoPriority = 0;
// 立即执行的任务 一般用来执行快过期的任务
export const ImmediatePriority = 1;
// 会阻塞渲染的优先级别，用户页面交互的
export const UserBlockingPriority = 2;
// 默认优先级 普通的优先级别
export const NormalPriority = 3;
// 低优先级别
export const LowPriority = 4;
// 空闲优先级
export const IdlePriority = 5;
```



### React SSR

1. React SSR是在什么场景下做的？

2. render和renderToString有什么区别？

## Redux

1. 工作流
2. 如何实现异步功能
3. 如何优化

