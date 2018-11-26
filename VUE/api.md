# api

## ref

[ref](https://cn.vuejs.org/v2/api/#ref)

`ref` 被用来给元素或子组件注册引用信息。

关于 `ref` 注册时间的重要说明：因为 `ref` 本身是作为渲染结果被创建的，在初始渲染的时候你不能访问它们 - 它们还不存在！

`$refs` 也不是响应式的，因此你不应该试图用它在模板中做数据绑定。

## 组件传值 props

[组件](https://cn.vuejs.org/v2/guide/components-props.html)

父组件使用子组件的props向子组件传值。

### 单向数据流

每次父级组件发生更新时，子组件中所有的 `prop` 都将会刷新为最新的值。这意味着你不应该在一个子组件内部改变 `prop`。

1.这个 `prop` 用来传递一个初始值；这个子组件接下来希望将其作为一个本地的 `prop` 数据来使用。

```javascript
props: ['initialCounter'],
data: function () {
  return {
    counter: this.initialCounter
  }
}
```

2.这个 `prop` 以一种原始的值传入且需要进行转换。在这种情况下，最好使用这个 `prop` 的值来定义一个计算属性:

```javascript
props: ['size'],
computed: {
  normalizedSize: function () {
    return this.size.trim().toLowerCase()
  }
}
```

### 非 Prop 的特性

因为显式定义的 `prop` 适用于向一个子组件传入信息，然而组件库的作者并不总能预见组件会被用于怎样的场景。这也是为什么组件可以接受任意的特性，

而这些特性会被添加到这个组件的根元素上。

对于绝大多数特性来说，从外部提供给组件的值会替换掉组件内部设置好的值。所以如果传入 type="text" 就会替换掉 type="date" 并把它破坏！

庆幸的是，class 和 style 特性会稍微智能一些，即两边的值会被合并起来，从而得到最终的值：form-control date-picker-theme-dark。

