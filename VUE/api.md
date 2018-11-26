# api

## ref

[ref](https://cn.vuejs.org/v2/api/#ref)

`ref` 被用来给元素或子组件注册引用信息。

关于 `ref` 注册时间的重要说明：因为 `ref` 本身是作为渲染结果被创建的，在初始渲染的时候你不能访问它们 - 它们还不存在！

`$refs` 也不是响应式的，因此你不应该试图用它在模板中做数据绑定。

## 组件传值 props

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
