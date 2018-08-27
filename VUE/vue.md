# vue

## 数据和方法

当一个 `Vue` 实例被创建时，它向 `Vue` 的响应式系统中加入了其 `data` 对象中能找到的所有的属性。当这些属性的值发生改变时，

视图将会产生“响应”，即匹配更新为新的值。除了数据属性，Vue 实例还暴露了一些有用的实例属性与方法。它们都有前缀 $，以便与用户定义的属性区分开来。

```javascript
// 我们的数据对象
var data = { a: 1 }

// 该对象被加入到一个 Vue 实例中
var vm = new Vue({
  data: data
})

// 获得这个实例上的属性
// 返回源数据中对应的字段
vm.a == data.a // => true

vm.$data === data // => true
vm.$el === document.getElementById('example') // => true
```

## 模板语法

### 特性

`Mustache` 语法不能作用在 `HTML` 特性上，遇到这种情况应该使用 `v-bind` 指令：

```html
<div v-bind:id="dynamicId"></div>
```

```html
<button v-bind:disabled="isButtonDisabled">Button</button>
```

如果 `isButtonDisabled` 的值是 `null`、`undefined` 或 `false`，则 `disabled`特性甚至不会被包含在渲染出来的 `<button>` 元素中。

##### input attribute 和 props 的区别

[原文链接](https://stackoverflow.com/questions/6003819/what-is-the-difference-between-properties-and-attributes-in-html#answer-6004028)

```html
<input type='text' value='a cute input'>
```

```javascript
input.value = 'value ...';
inpput.getAttribute('value') = 'a cute input';
input.getDefaultValue = 'a cute input';
```

### 指令

指令特性的值预期是单个 `JavaScript` 表达式.

#### 参数

一些指令能够接收一个“参数”，在指令名称之后以冒号表示。

```html
<a v-bind:href="url">...</a>
```

在这里 `href` 是参数，告知 `v-bind` 指令将该元素的 `href` 特性与表达式 `url` 的值绑定。

#### 修饰符

修饰符 `(Modifiers)` 是以半角句号 . 指明的特殊后缀，用于指出一个指令应该以特殊方式绑定。例如，

`.prevent` 修饰符告诉 `v-on` 指令对于触发的事件调用 `event.preventDefault()：`

```html
<form v-on:submit.prevent="onSubmit">...</form>
```

## 计算属性和侦听器

### 计算属性缓存 vs 方法

`计算属性`是基于它们的依赖进行缓存的。计算属性只有在它的相关依赖发生改变时才会重新求值。

这就意味着只要 `message` 还没有发生改变，多次访问 `reversedMessage` 计算属性会立即返回之前的计算结果，而不必再次执行函数。

## Class 与 Style 绑定

### 绑定Class

#### 对象语法

我们可以传给 `v-bind:class` 一个对象，以动态地切换 `class`

```html
<div v-bind:class="{ active: isActive }"></div>
```

上面的语法表示 `active` 这个 `class` 存在与否将取决于数据属性 `isActive` 的 `truthiness`。

我们也可以在这里绑定一个返回对象的计算属性。

```html
<div v-bind:class="classObject"></div>
```

```javascript
data: {
  isActive: true,
  error: null
},
computed: {
  classObject: function () {
    return {
      active: this.isActive && !this.error,
      'text-danger': this.error && this.error.type === 'fatal'
    }
  }
}
```

#### 数组语法

我们可以把一个数组传给 `v-bind:class`，以应用一个 `class` 列表：

```html
<div v-bind:class="[activeClass, errorClass]"></div>
```

```javascript
data: {
  activeClass: 'active',
  errorClass: 'text-danger'
}
```

#### 用在组件上

当在一个自定义组件上使用 `class` 属性时，这些类将被添加到该组件的根元素上面。这个元素上已经存在的类不会被覆盖。

### 绑定内联样式

`v-bind:style` 的对象语法十分直观——看着非常像 `CSS`，但其实是一个 `JavaScript` 对象。`CSS` 属性名可以用驼峰式 (camelCase) 

或短横线分隔 (kebab-case，记得用单引号括起来) 来命名：

```javascript
<div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>

<div v-bind:style="styleObject"></div>
```

#### 自动添加前缀

## 条件渲染

### 用<tempalte>元素 使用 v-if 指令分组

因为 `v-if` 是一个指令，所以必须将它添加到一个元素上。但是如果想切换多个元素呢？此时可以把一个 `<template>` 元素当做不可见的包裹元素，

并在上面使用 `v-if`。最终的渲染结果将不包含 `<template>` 元素。

### 用 key 管理可复用的元素

 `Vue` 为你提供了一种方式来表达“这两个元素是完全独立的，不要复用它们”。只需添加一个具有唯一值的 `key` 属性即可：
 
 ### v-show
 
 另一个用于根据条件展示元素的选项是 `v-show` 指令。
 
 不同的是带有 `v-show` 的元素始终会被渲染并保留在 `DOM` 中。`v-show` 只是简单地切换元素的 `CSS` 属性 `display`。
 
 ### v-if vs v-show
 
 `v-if` 是“真正”的条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。
 
 `v-show` 就简单得多——不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 `CSS` 进行切换。
 
 如果需要非常频繁地切换，则使用 `v-show` 较好；如果在运行时条件很少改变，则使用 `v-if` 较好。
 
 `v-for`拥有比`v-if`更高的优先级。
 
 ## 列表渲染
 
 在 `v-for` 块中，我们拥有对父作用域属性的完全访问权限。`v-for` 还支持一个可选的第二个参数为当前项的索引。
 
 ### 一个对象的 v-for
 
 第二个的参数为键名,第三个参数为索引。
 
 ```html
 <div v-for="(value, key) in object">
  {{ key }}: {{ value }}
</div>
```

```javascript
new Vue({
  el: '#v-for-object',
  data: {
    object: {
      firstName: 'John',
      lastName: 'Doe',
      age: 30
    }
  }
})
```

#### 注意事项

由于 `JavaScript` 的限制，`Vue` 不能检测以下变动的数组：

当你利用索引直接设置一个项时，例如：vm.items[indexOfItem] = newValue

当你修改数组的长度时，例如：vm.items.length = newLength

```javasvript
// Vue.set
Vue.set(vm.items, indexOfItem, newValue)

// Array.prototype.splice
vm.items.splice(indexOfItem, 1, newValue)
```

### 一个组件的 v-for

任何数据都不会被自动传递到组件里，因为组件有自己独立的作用域。为了把迭代数据传递到组件里，我们要用 `props` ：

## 事件处理

## 表单输入绑定

可以用 `v-model` 指令在表单 `<input>` 及 `<textarea>` 元素上创建双向数据绑定。

## 深入了解组件

### data 必须是一个函数

一个组件的 data 选项必须是一个函数，因此每个实例可以维护一份被返回对象的独立的拷贝：

```javascript
data: function () {
  return {
    count: 0
  }
}
```



这个 .passive 修饰符尤其能够提升移动端的性能。
