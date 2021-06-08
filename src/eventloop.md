## 什么是event loop

Event Loop是一个很重要的概念，指的是计算机系统的一种运行机制。

在wikipedia中这样定义的：

> Event Loop是一个程序结构，用于等待和发送消息和事件

简单来说，就是在程序中设置两个线程：一个负责程序本身的运行，称为“主线程”；另一个负责主线程和其他线程的通信，被称为“Event Loop线程”

## JavaScript运行机制

### 单线程的JavaScript

JavaScript语言的一大特点就是单线程，也就是同一时间只做同一件事儿

### JavaScript中的任务队列

JavaScript是单线程的，意味着所有任务需要排队，前一个任务执行完才能执行下一个任务。同时JavaScript将任务分为同步任务和异步任务。同步任务是指在主线程排队的任务，只有前面的任务执行完之后才执行后面的任务。异步任务指的是任务不进入主线程，而进入到一个任务队列，主线程的任务可以继续往后执行，而在任务队列中的异步任务执行完会通知主线程

## 浏览器的event loop

### 执行栈和事件队列

当所有的同步任务都在主线程上执行时，这些任务被排列在一个单独的地方，形成一个执行栈



当浏览器js引擎解析这段代码时，会将同步任务顺序加入执行栈中依次执行，当遇到异步任务时并不会一直等待异步任务返回结果再执行后面的任务，而是将异步任务挂起，继续执行同步任务，当异步任务返回结果时，将异步任务的回调事件加入到一个事件队列当中去，这个事件队列的任务并不会立即执行，而是等同步任务全部执行完，再依次执行事件队列里的事件。



依次执行同步任务，完成后依次执行事件队列，完成后再去执行同步任务，这样形成了一个循环，就是事件循环

### 宏任务和微任务

## node的event loop

- timers：执行定时器队列中的回调，如setTimeout()和setInterval()
- I/O callbacks：执行几乎所有的回调，但是不包括close事件，定时器和setImmediate的回调
- idle，prepare：内部使用，不必理会
- poll：等待新的I/O事件，node在一些特殊情况下回阻塞在这里
- check：setImmediate()的回调会在这个阶段执行
- close callbacks：例如socket.on('close', fn)这种close事件的回调



## 相关链接

- [https://html.spec.whatwg.org/multipage/webappapis.html#event-loops](https://html.spec.whatwg.org/multipage/webappapis.html#event-loops)
- [NodeJs的libuv实现的event loop](http://docs.libuv.org/en/v1.x/design.html)

