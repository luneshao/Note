# Vue Loader 笔记

## 共享全局变量

`sass-loader` 也支持一个`data`选项，这个选项允许你在所有被处理的文件之间共享常见的变量，而不需要显式地导入它们：

```javascript
// webpack.config.js -> module.rules
{
  test: /\.scss$/,
  use: [
    'vue-style-loader',
    'css-loader',
    {
      loader: 'sass-loader',
      options: {
        // 你也可以从一个文件读取，例如 `variables.scss`
        data: `$color: red;`
      }
    }
  ]
}
```
 
## Scoped CSS

当 <style> 标签有 scoped 属性时，它的 CSS 只作用于当前组件中的元素。

```html
<style scoped>
.example {
  color: red;
}
</style>

<template>
  <div class="example">hi</div>
</template>
```
### 子组件的根元素

    使用 scoped 后，父组件的样式将不会渗透到子组件中。不过一个子组件的根节点会同时受其父组件的 scoped CSS 和
    子组件的 scoped CSS 的影响。这样设计是为了让父组件可以从布局的角度出发，调整其子组件根元素的样式
