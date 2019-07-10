# Nodejs 学习笔记

## assert断言

### 1. assert.AssertionError 类

`Error` 的子类，表明断言的失败。`assert` 模块抛出的错误都是 `AssertionError` 这个类的实例。

### 2. 严格模式

当使用严格模式时，`assert` 中的任何函数都将使用严格函数模式中使用的相等性。即 assert.deepEqual() 将与 assert.deepStrictEqual() 一样效果。使用方式如下：

```js
  const assert = require('assert').strict;
```

note：严格模式下当抛出错误时，将会明确存在差异的位置。

### 3. assert(value[, message])

* value：判断 value 是否为 `true`
* message `<string> | <Error>`：自定义输出的错误文本和错误类型，若未分配则展示错误的位置。

assert.ok() 的别名。

### 4. assert.ok(value[, message])

测试 value 是否为真值

### 5. assert.deepEqual(actual, expected[, message]) (已弃用）

* actual：对比的值
* expected：被对比的值
* message：自定义的错误，如果提供，则将错误消息设置为此值。

**严格模式**：assert.deepStrictEqual()

### 6. assert.deepStrictEqual(actual, expected[, message])

严格模式下 actual 和 expected 深度相等。

### 7. assert.strictEqual(actual, expected[, message])

测试 actual 参数和 expected 参数之间的严格相等性，使用 SameValue比较。

### 8. assert.notDeepStrictEqual(actual, expected[, message])

严格模式下深度测试两个值不相等。（可以测试对象是否严格相等）

### 9. assert.notStrictEqual(actual, expected[, message])

严格模式下测试 actual 参数和 expected 参数之间的严格不相等，使用 SameValue比较。

### 10. assert.doesNotReject(asyncFn[, error][, message])

* asyncFn：被检测函数。

捕获 promise 的 reject,返回一个 promise，reject 中包含了错误信息。除了等待的异步性质之外，完成行为与 assert.doesNotThrow() 完全相同。

这里我写了一个例子，反复测没测通，总是立马被捕获，不能到 assert.doesNotReject 的 reject 中，我已经找到问题出在哪里了，但是没弄明白为什么。贴一下：

```js
function func1 () {
  return new Promise((res, rej) => {
    setTimeout (() => {
      throw new Error()
    }, 1000)
  })
}

assert.doesNotReject(func1)
  .then(res => {
    console.log('hi')
  })
  .catch(err => {
    console.log('hello')
  })
```

看看你能找到错在哪里了吗？然后，请指教为何这样就不会被 assert.doesNotReject 捕获。

### 11. assert.rejects(asyncFn[, error][, message])

期望 asyncFn 抛出错误。如果有错误，会执行 promise 的 then 方法。除了等待的异步性质之外，完成行为与 assert.throws() 完全相同。

```
function func1 () {
  return new Promise((res, rej) => {
      throw new Error()
  })
}


assert.rejects(func1)
  .then(res => {
    console.log('hi')
  })
  .catch(err => {
    console.log('hello')
  })
  
output: hi
```

### 12. assert.doesNotThrow(fn[, error][, message])

断言 fn 函数不会抛出错误。

### 14. assert.throws(fn[, error][, message])

期望 fn 函数抛出错误。

### 13. assert.fail([message])

使用提供的错误消息或默认错误消息抛出 AssertionError。如果 message 参数是 Error 的实例，则它将被抛出而不是 AssertionError。

### 14. assert.ifError(value)

如果 value 不为 undefined 或 null，则抛出 value。即 value 有值，就会抛出一个错误，值为 value。


