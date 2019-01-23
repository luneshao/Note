# vue-router

将组件 (components) 映射到路由 (routes)，然后告诉 Vue Router 在哪里渲染它们。

## vue-router 钩子函数

### 全局钩子函数

[原文链接](https://www.jianshu.com/p/96cfc1b9ff21)

```jvascript
beforeEach（to，from，next）
afterEach（to，rom，next）
```

### 组建内的导航钩子

组件内的导航钩子主要有这三种：`beforeRouteEnter`、`beforeRouteUpdate`、`beforeRouteLeave`。他们是直接在路由组件内部直接进行定义的。

