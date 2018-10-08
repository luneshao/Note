# vue延伸及遇到的问题

## 1.vue监听resize事件

[原文链接](http://www.cnblogs.com/erbingbing/p/6340930.html)

### 方法一

* 步骤一：data 添加浏览器宽的初始值

```javascript
data(){
  curClientW : document.body.clientWidth
}
```

* 步骤二：mounted 时挂载 resize 方法

```javascript
 mounted () {
  const that = this
  window.onresize = () => {
    return (() => {
        window.screenWidth = document.body.clientWidth
        that.screenWidth = window.screenWidth
    })()
  }
}
```

* 步骤三：watch 监听窗口的改变，执行操作

```javascript
watch: {
  screenWidth (val) {
    this.screenWidth = val
  }
}
```

* 步骤四： 优化

watch: {
  screenWidth (val) {
    if (!this.timer) {
      this.screenWidth = val
      this.timer = true
      setTimeout(function () {
        that.timer = false
      }, 400)
    }
  }
}

### 方法二

在`vue 2.x` 里面的时候，可以在 `mounted` 钩子中 全局监听 `resize` 事件，然后绑定的函数再做具体的处理。
