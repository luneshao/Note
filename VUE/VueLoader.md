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
    
### 语言块
 
`<template>`

* 默认语言：`html` 。

* 每个 `*.vue` 文件几乎都包含一个 `<template>` 块。

* `<template>` 内的内容字符串会被提取出来，用来编译进 `Vue` 组件内的 `template` 选项。
  
`<script>`

* 默认语言：`js`（默认ES2015也会通过Babel支持）。

* 每个 `*.vue` 文件几乎都包含一个 `<script>` 块。

* 脚本就像在`CommonJS`的环境中一样被执行（就像通过WebPACK中捆绑一个正常的`.js`模块）。就是说你可以 `require()` 其他的依赖项。

  由于默认支持 `ES2015` ，你也可以用 `import` 和 `export` 语法。

* 该脚本必须导出一个 `Vue.js` 组件选项对象，也支持导出一个用 `Vue.extend()` 创建的扩展构造函数，但首先是导出普通对象。
    
### ES6
  
  当 `vue-loader` 检测到 `babel-loader` 或者` buble-loader` 在项目中存在的时候，将会用它们去处理所有 `*.vue`
  
  文件的 `<script>` 部分，所以我们就可以在 `Vue` 组件中用 `ES2015` 。
  
```javascript
<script>
import ComponentA from './ComponentA.vue'
import ComponentB from './ComponentB.vue'

export default {
  components: {
    ComponentA,
    ComponentB
  }
}
</script>
```

在这里用的就是 `ES2015` 精简的语法定义个子组件。`{ ComponentA }` 是指 `{ ComponentA: ComponentA }` 。

Vue会被自动转为 `component-a`， 所以你就能在模板中引入组件 `<component-a>` 。

### scoped 属性

当 `<style>` 标签有 `scoped` 属性的时候，它的 `CSS` 就只能作用于当前的组件。这就像样式被封装在 `Shadow DOM` 内。这是用 `PostCSS` 转译实现的。
