

当我们在浏览器中输入url，底层会进行一些神奇的操作，然后将一些文档资源渲染到浏览器页面中

现在我们就来看下有哪些神奇的操作吧

1. 用户输入url，会向DNS服务器（域名解析系统）发送一个请求，获取当前url（域名）对应的IP地址，找到后系统会向对应的IP地址的网络服务器发送一个http请求
2. 网络服务器解析请求，并发送请求到数据库服务器
3. 数据库服务器将请求的资源，网络服务器解析数据，生成html文件，返回给浏览器
4. 浏览器解析返回的数据，下载html文件，以及html中引用的外部文件，图片等多媒体文件

### 资源加载阶段

在html文件加载过程中会遇到css或者图片，但是这些资源都不会影响html的加载

但是遇到js文件，html文档就会挂起渲染的线程，等待文档中的js文件加载完，且解析执行完毕才可以恢复

虽然css文件的加载不影响js文件的加载，但是却影响js文件的执行

### 解析阶段

html文件解析成DOM tree

css文件解析成CSS Rule tree

JavaScript脚本加载后，会通过DOM API和CSS DOM API来操作DOM Tree和CSS Rule Tree

### 渲染阶段

渲染树就是DOM树的可视化表示

**渲染树和DOM树：**

不可见的dom元素不会插入渲染树中，还有一些节点位置为绝对或浮动定位的节点会在文本流之外

**渲染过程：**

1. 浏览器引擎将DOM Tree和CSS Rule Tree构建Rendering Tree
2. 但是Rendering Tree并不与DOM Tree对应，比如`<head>`标签内容或带有`display:none;`的元素节点并不包括在Rendering Tree中
3. 通过CSS Rule Tree匹配DOM Tree进行定位坐标和大小，是否换行，以及position、overflow、z-index等属性的过程叫做Flow或Layout
4. 通过Native GUI的API绘制网页画面的过程称为Paint

