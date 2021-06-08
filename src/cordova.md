

### 问题集

**1.cordova create报错**

问题详情：提示`_cordova-app-hello-world@3.12.0@cordova-app-hello-world\index.js as it does not contain a package.json file`

解决方法：

cnpm安装会丢包，所以使用npm安装，并设置淘宝镜像

```sh
npm install -g cordova --registry=https://registry.npm.taobao.org
```

