

### 观察者模式

> 定义了对象间的一种一对多的依赖关系，当目标对象Subject状态发生改变时，所有依赖它的Observer都会发生改变

#### 特征

1. 一个目标对象`Subject`，拥有添加/删除/通知`Observer`
2. 多个观察对象`Observer`，拥有方法，接收`Subject`状态变更通知并处理
3. 目标对象`Subject`状态变更时，通知所有`Observer`

#### 实现

```js
class Subject {
  constructor() {
    this.observers = [];
  }
  add(observer) {
    this.observers.push(observer);
  }
  remove(observer) {
    let idx = this.observers.findIndex(item => item === observer);
    idx > -1 && this.observers.splice(idx, 1);
  }
  notify() {
    for (let observer of this.observers) {
      observer.update();
    }
  }
}
```

#### 优势

- 目标者和观察者，功能耦合度降低，专注自身功能逻辑
- 观察者被动接收更新，时间上解耦，实时接收目标者更新状态

### 发布订阅者模式

> 基于一个事件通道，希望接收通知的对象Subscriber通过自定义事件订阅主题，被激活事件对象Publisher通过发布主题事件的方式通知各个订阅该主题的Subscriber对象

#### 实现

```js
let pubSub = {
  list: {},
  subscribe: function(key, fn) {
    if (!this.list[key]) {
      this.list[key] = [];
    }
    this.list[key].push(fn);
  },
  publish: function(key, ...arg) {
    for (let fn of this.list[key]) {
      fn.call(this, ...arg);
    }
  },
  unSubscribe: function(key, fn) {
    let fnList = this.list[key];
    if (!fnList) return false;
    if (!fn) {
      fnList && (fnList.length = 0)
    } else {
      fnList.forEach((item, index) => {
        if (item === fn) {
          fnList.splice(index, 1)
        }
      })
    }
  }
}
```

