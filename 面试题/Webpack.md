

#### 1.Loader和Plugin的区别

```markdown
Loader本质是一个函数，在函数中对接收到的内容进行转换，返回转换后的结果
Plugin就是插件，基于事件流框架`Tapable`，插件可以拓展webpack功能，在webpack运行的生命周期中会广播出许多事件，Plugin可以监听这些事件
```

#### 2.webpack的构建流程

```markdown
1. 初始化参数：从配置文件和shell语句中读取与合并参数
2.开始编译：用上一步的参数初始化compiler对象，加载所有配置的插件，执行对象的run方法开始执行编译
3.确定入口：根据entry找出所有入口文件
4.编译模块：从入口文件开始，调用所有配置的loader对模块进行编译，再找出该模块依赖的其他模块，递归本步骤知道所有入口依赖的文件都经过了本步骤处理
5.完成模块编译：得到所有模块被编译后的最终内容以及模块之间的依赖关系
6.输出资源：根据入口与模块的依赖关系，组装成一个个包含多个模块的chunk，再把每个chunk转换成一个单独的文件加入到输出列表
7.输出完成
```

#### 3.source map是什么？生产环境怎么用？

```markdown
source map是将编译、打包、压缩后的代码映射回源代码的过程。打包压缩后的代码不具备良好的可读性，想要调试源码就需要 soucre map。
线上环境方案：
1. hidden-source-map：借助第三方错误监控平台sentry使用
2.nosources-source-map：只会显示具体行数以及查看源代码的错误栈
3.sourcemap：通过 nginx 设置将 .map 文件只对白名单开放(公司内网)
```

#### 模块打包原理

```markdown
暂无
```

#### 文件监听原理

```markdown
在发现源码发生变化时，自动重新构建出新的输出文件

缺点：每次需要手动刷新浏览器
原理：轮询判断文件的最后编辑时间是否变化，如果某个文件发生了变化，并不会立刻告诉监听者，而是先缓存起来，等aggregateTimeout候再执行
```

#### webpack热更新原理

```markdown
热更新就是可以做到不用刷新浏览器就可以将新的模块替换旧的模块

1. WDS与浏览器之间维护了一个Websocket，当本地资源发生变化时，WDS会向浏览器推送更新，并带上构建时的hash，让客户端与上一次资源进行比较。
2. 客户端对比出差异后会向WDS发起ajax请求来获取更改内容
3. 客户端再借助这些信息继续向WDS发起jsonp请求获取该chunk的增量更新
```

#### 如何保证loader按照预想的方式工作

```markdown
使用enforce强制执行loader的作用顺序
pre代表在所有正常loader之前执行
post是所有loader之后执行
```

#### 如何优化webpack的构建速度

```markdown
1. 使用高版本的webpack和nodejs
2. 多进程构建：thread-loader
3. 压缩代码
4. 图片压缩
5. 缩小打包作用域
6. 提取公共资源（SplitChunksPlugin、hhtml-webpack-externals-plugin
7. DLL （分包，将基本不会改的代码先打包成静态资源）
8. 充分利用缓存提升二次构建速度（babel-loader、terser-webpack-plugin、cache-loader）
9. Tree shaking（标记没引用的模块，在最终bundle中删除，禁用babel-loader的模块依赖解析，去除无用css代码）
10. Scope hoisting （
```

