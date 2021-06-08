## setup



### provide/inject

众所周知，provide/inject两个属性可以用作多层组件传值，那么如何在vue3.0的setup中使用呢？

```typescript
// 顶层组件，输入provide
import { defineComponent, provide } from 'vue'
export default defineComponent({
  setup(props, context) {
    // provide第一个参数是传入的数据的名称，第二个参数是值
    provide('name', value)
  }
})

// 低层级组件，获取inject
import { defineComponent, inject } from 'vue'
export default defineComponent({
  setup(props, context) {
    // inject第一个参数是需要获取的数据名称，第二个参数是默认值
    const name = inject('name', defaultValue)
  }
})
```

### slots

slots作为插槽，其基本使用方式兼容vue2.x，但是我想说的是vue3.0的新版使用方式，代码如下所示：

```typescript
import { defineComponent, h } from 'vue'
export default defineComponent({
  setup(props, { slots }) {
    return () => h('div', { class: ['comp-name']}, slots.default?.())
  }
})
```

