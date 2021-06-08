> setState()`将对组件的更改排入队列，并通知React需要使用更新后的state重新渲染此组件以及子组件。

在官网中说了setState是用于更新用户界面以响应事件处理器和处理服务器数据的主要方式

且我们可以将`setState()`视为**请求**而不是立即更新组件的命令

之所以可以视为**请求**，我想是因为react当中不会保证state的变更会立即生效，在React当中会延迟调用，通过一次传递更新多个组件

如果想获取setState更新后的数据，一种方式是通过`setState(updater, callback)`中的callback获取更新后的state，另一个种方式是使用componentDidUpdate中获取

对于setState，我们需要带着如下问题学习：

1. setState是同步还是异步?为什么这样设计？

## 使用方式

1. `#setState(updater[, callback])`

updater的形式有两种，一种是对象，一种是函数

对象形式的变更无需多说，我们讲一讲函数式的

函数式`updater = (state, props) => {}`，函数中的参数state以及props都为最新的。

updater的返回值会与`state`进行一个浅合并

2. `#setState((state, props) => updater[, callback])`

## 执行流程

1. 当调用setState时，会执行enqueueSetState方法，找到当前修改组件对应的Fiber节点，并且将需要修改的状态添加到update对象上，将update传入到enqueueUpdate方法中
2. 找到fiber节点的更新队列，
3. 判断当前是否处于批量更新阶段，如果是就将当前更新组件加入dirtyComponent中，如果不是就执行更新batchedUpdate
4. 发起一次transaction.perform()事务

## 同步or异步

其实setState虽然看着像是异步的，但是其本质是同步执行的

不过在生命周期或者合成事件中执行的时机是异步的，而在setTimeout或者原生事件中就是同步执行（执行后马上就能取到最新值）

### 钩子函数和合成事件中

在这两个阶段中，react仍然处于更新机制中，这时`isBatchingUpdate`为true

在这个时候，无论调用多少次`setState`，都不会执行更新，而是将要更新的`state`存入待更新队列中，将要更新的组件出入`dirtyComponent`

## 注意

### componentDidMount中调用setState

在这个生命钩子中使用setState，这个时候本身就处于一次更新中，再调用一次setState，就会在之后再进行一次render，造成不必要的性能浪费，大多数情况下可以设置初始值来搞定

正确的做法是：在componentDidMount中可以调用接口，在回调中修改state

### componentWillUpdate和componentDidUpdate

在上述两个生命周期中不能调用setState，如果调用会造成死循环，导致程序崩溃