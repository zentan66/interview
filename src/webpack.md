

## 配置source-map

source-map就是源码映射，主要是为了方便代码调试。因为我们打包上线后的代码会被压缩等处理，导致所有代码都被压缩成了一行，如果代码中出现错误，那么浏览器只会提示出错位置在第一行，无法真正知道出错地方在源码中的具体位置。

### source-map

这种模式的特点是会产生一个**.map**文件，文件里面保留了打包后的文件与原始文件之间的映射关系，能够通过map文件逆向解析出源码内容，出错了能够提示到具体的行和列

### eval

这种模式打包速度最快，不会生成**.map**文件，会使用eval将模块包裹，在末尾加入sourceURL

### eval-source-map

每个module会通过eval()来执行，并生成一个DataUrl形式的sourcemap，但是不会生成.map文件，可以减少网络请求，浏览器中点击报错文件链接，光标可以定位到源码中出错位置的行和列，打包文件会非常大

### cheap-source-map

相比较source-map而言，只会提示到第几行报错，少了列信息提示，可以提高打包性能，但是仍然会产生.map文件，并且其解析到的是经过loader转换后的代码

### cheap-module-source-map

相比较cheap-source-map，报错的时候定位到的是loader转换前的源码位置，会产生.map文件

### Cheap-module-eval-source-map

使用cheap模式可以大幅提高sourcemap生成的效率，加上module可以定位到源码经过loader转换前的位置，eval提高打包构建速度，并且不会产生.map文件，减少网络请求

## 优化

### 优化开发体验

1. 优化构建速度：缩小文件搜索范围、DllPlugin、HappyPack、ParallelUglifyPlugin
2. 优化使用体验：通过自动化手段，实现自动刷新和模块热替换

### 优化输出质量

1. 减少用户能感知的加载时间：区分环境、压缩、提取公共代码、按需加载、CDN、Tree Shaking
2. 提升流畅度：prepack、scope hoisting



## 参考链接

1. [一看就懂之webpack高级配置与优化](https://segmentfault.com/a/1190000020320871?utm_source=weekly&utm_medium=email&utm_campaign=email_weekly)