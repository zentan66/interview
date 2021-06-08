### vue部分

**长列表优化**

对于纯粹的数据显示，不需要vue劫持，为了减少组件初始化的时间，可以使用`Object.freeze`冻结对象

```js
export default {
  data() {
    return {
      users: {}
    }
  },
  async created() {
    const users = await axios.get('/api/users')
    this.users = Object.freeze(users)
  }
}
```

**事件销毁**

通过`addEventListener`绑定的事件监听器，并不会自动销毁，所以需要在组件销毁时，手动处理

**图片资源懒加载**

**路由懒加载**

```js
const Foo = () => import('./Foo.vue')
```

**第三方插件按需引入**

借助`babel-plugin-component`按需引入组件

```json
{
  "presets": [["es2015", { "modules": false }]],
  "plugins": [
    [
      "component",
      {
        "libraryName": "element-ui",
        "styleLibraryName": "theme-chalk"
      }
    ]
  ]
}
```

**优化无限列表性能**

应用存在非常长或无限滚动的列表，使用窗口化技术优化性能，减少重新渲染组件和创建dom节点的时间

`vue-virtual-scroll-list`或`vue-virtual-scroller`

**服务端渲染or预加载**

### webpack部分

**图片压缩**

对于较大的图片可以使用`image-webpack-loader`压缩图片

**提取公共代码**

**模板预编译**

**提取组件css**

**优化sourcemap**

**构建结果输出分析**

`webpack-bundle-analyzer`

