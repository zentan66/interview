

## 解析器

### 文本解析器

1. HTML解析器

```javascript
parseHtml(template, {
  start(){},
  end(){},
  chars() {},
  comment() {}
})
```

2. 解析到文本时触发chars函数，接收text

```javascript
/**
* example text = "hello {{name}}"
*/
function chars(text) {
  // expression = "hello" + _s(name)
  if (expression = parseText(text)) {
    children.push({
      type: 2,
      expression,
      text
    })
  } else {
    children.push({
      type; 3,
      text
    })
  }
}
```



## 优化器

> 在AST中找出静态节点并打上标记

优化器内部实现步骤：

1. 在AST中找出所有静态节点并打上标记
2. 在AST中找出所有静态根节点并打上标记

静态节点：static属性是true的 根据节点的type判断，3是静态节点

静态根节点：staticRoot属性是true的

### 	QA

1. 标记静态节点的好处

```
- 每次重新渲染，不需要为静态子树创建新节点
- 在虚拟DOM中打补丁的过程可以跳过
```

