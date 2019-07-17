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

## async_hooks（异步钩子）

### 1. async_hooks.createHook(callbacks)

* callbacks：注册钩子回调

    * init
    * before
    * after
    * destroy
    
* Returns：返回一个 async_hooks 的实例，用于采用和禁用跟踪。

⚠️ callbacks 通过原型链会被继承。

### 2. asyncHook.enable()

* Returns：返回一个 asyncHook 的引用

为 asyncHook 启用回调。

```js
const async_hooks = require('async_hooks');

const hook = async_hooks.createHook(callbacks).enable();
```

### 3. asyncHook.disable()

* Returns：返回一个 asyncHook 的引用

为 asyncHook 禁用回调。

### 4. 钩子回调

共分为四类 instantiation, before/after 回调被调用, 和实例被销毁 destroyed.

* init (asyncId, type, triggerAsyncId, resource)

    * asyncId：异步资源唯一的ID
    * type：异步资源的类型
    * triggerAsyncId：在创建 asyncHook 实例时执行的上下文的创建资源的ID
    * resourceL：代表了异步操作资源的引用，需要在销毁期间释放。
    
当一个类被构造后，有可能会发出异步事件时被调用。

#### type

是一个字符串，用来表示调用 init 的资源的类型。通常，它对应于资源构造函数的名称。

#### triggerAsyncId

触发新资源初始化并导致 init 调用的资源的 asyncId。

#### resource

是一个对象，代表了已经初始化的实际的异步资源。

* before(asyncId)

当启动异步操作或完成磁盘读写时，将调用回调通知用户。before 回调将在执行回调前被调用。asyncId 分配给执行回调的资源。

* after(asyncId)

在完成 before 指定的回调后立即调用。

* destroy(asyncId)

在与 asyncId 对应的资源被销毁后被调用。也会被嵌入器的 API emitDestroy() 异步调用。一些资源依赖垃圾收集进行清理，如果对传递给 init 中的资源进行引用，那么资源将永远不会被回收，从而导致内存泄漏。

* promiseResolve(asyncId)

当传递给 Promise 构造函数的 resolve 函数时调用。如果 Promise 使用另一个 Promise 状态作为 resolve，那么 Promise 将不会得到被响应res 或 rej。

### 5. async_hooks.executionAsyncId()

* Returns：返回当前执行的上下文的 asyncId

### 6. async_hooks.triggerAsyncId()

* Returns：当前正在被执行的回调的ID

## Buffer

在引入 TypedArray 之前，JavaScript 语言没有用于读取或操作二进制数据流的机制。 Buffer 类是作为 Node.js API 的一部分引入的，用于在 TCP 流、文件系统操作、以及其他上下文中与八位字节流进行交互。

* Buffer 实例也是 Uint8Array 实例，但是与 TypedArray 有微小的不同。 例如，ArrayBuffer#slice() 会创建切片的 _拷贝_ ，而 Buffer#slice() 是在现有的 Buffer 上 _创建_ 而不拷贝，这使得 Buffer#slice() 效率更高。

## fs

* 用于以模仿标准 POSIX 函数的方式与文件系统进行交互。
* 大多数 fs 操作接受的文件路径可以指定为字符串、Buffer、或使用 file: 协议的 URL 对象。
* 在 Windows 上，Node.js 遵循每个驱动器工作目录的概念。 当使用没有反斜杠的驱动器路径时，可以观察到此行为。
* WHATWG URL 对象，仅支持使用 file: 协议的 URL 对象。
    * 除 Windows 外，在所有其他平台上，不支持带有主机名的 file: URL，使用时将导致抛出错误。
    * 包含编码后的斜杆字符（%2F）的 file: URL 在所有平台上都将导致抛出错误。

### 1. fs.open()

Node.js 抽象出操作系统之间的特定差异，并为所有打开的文件分配一个数字型的文件描述符。

fs.open() 方法用于分配新的文件描述符。

### 2. 线程池的使用

线程池就是对线程的统一管理，预先创建出线程，如果有任务就把任务放到线程池里去执行。

所有的文件系统 API，除了 fs.FSWatcher() 和那些显式同步的之外，都使用 [libuv](https://zhuanlan.zhihu.com/p/50497450) 的线程池，这对某些应用程序可能会产生意外和负面的性能影响。

### 3. fs.Dirent 类

当使用 withFileTypes 选项设置为 true 调用 fs.readdir() 或 fs.readdirSync() 时，生成的数组将填充 fs.Dirent 对象，而不是字符串或 Buffer。

实例判断 fs.Dirent 对象描述类型：块设备、字符设备、文件系统目录、FIFO、常规文件、套接字、描述符号链接、文件名。

### 4. fs.FSWatcher 类

成功调用 fs.watch() 方法将返回一个新的 fs.FSWatcher 对象。

* change 事件：每当修改指定监视的文件，就会触发 'change' 事件。
    * eventType：
    * filename
* close 事件
* error 事件
* watcher.close()：给定的 fs.FSWatcher 停止监视更改。

### 5. fs.ReadStream 类

成功调用 fs.createReadStream() 将返回一个新的 fs.ReadStream 对象。所有 fs.ReadStream 对象都是可读流。

* close 事件：当 fs.ReadStream 的底层文件描述符已关闭时触发。
* open 事件：当 fs.ReadStream 的文件描述符打开时触发。
* ready 事件：'open' 事件之后立即触发。

readStream.bytesRead：到目前为止已读取的字节数。
readStream.path：流正在读取的文件的路径，由 fs.createReadStream() 的第一个参数指定。
readStream.pending：在触发 ready 前未打开文件，则返回 true。

### 6. fs.Stats 类

fs.Stats 对象提供有关文件的信息。

实例判断 fs.Stats 对象描述类型：块设备、字符设备、文件系统目录、FIFO、常规文件、套接字、符号链接。

* stats.dev：包含该文件的设备的数字标识符。
* stats.ino：文件系统特定的文件索引节点编号。
* stats.mode：描述文件类型和模式的位字段。
* stats.nlink：文件存在的硬链接数。
* stats.uid：拥有该文件（POSIX）的用户的数字型用户标识符。
* stats.gid：拥有该文件（POSIX）的群组的数字型群组标识符。
* stats.rdev：如果文件被视为特殊文件，则此值为数字型设备标识符。
* stats.size：文件的大小。
* stats.blksize：用于 I/O 操作的文件系统块的大小。
* stats.blocks：为此文件分配的块数。
* stats.atime（Ms）：上次访问此文件的时间戳，（以 POSIX 纪元以来的毫秒数表示）。
* stats.mtime（Ms）：表明上次修改此文件的时间戳，（以 POSIX 纪元以来的毫秒数表示）。
* stats.ctime（Ms）：表明上次更改文件状态的时间戳，（以 POSIX 纪元以来的毫秒数表示）。
* stats.birthtime（Ms）：创建时间的时间戳，（以 POSIX 纪元以来的毫秒数表示）。
    * atimeMs、 mtimeMs、 ctimeMs 和 birthtimeMs 属性是保存相应时间（以毫秒为单位）的数值。 它们的精度取决于平台。
    * atime、 mtime、 ctime 和 birthtime 是对应时间的 Date 对象。
    
### 7. fs.WriteStream 类

WriteStream 是一个可写流。事件类型同上。

### 8. fs.access(path[, mode], callback)

测试用户对 path 指定的文件或目录的权限。

### 9. fs.appendFile(path, data[, options], callback)

异步地将数据追加到文件，如果文件尚不存在则创建该文件。 data 可以是字符串或 Buffer。

### 10. fs.chmod(path, mode, callback)

异步地更改文件的权限。

### 11. fs.chown(path, uid, gid, callback)

异步地更改文件的所有者和群组。

### 12. fs.createReadStream(path[, options])

* 如果指定了 fd，则 ReadStream 将忽略 path 参数并使用指定的文件描述符。 这意味着不会触发 'open' 事件。 fd 必须是阻塞的，非阻塞的 fd 应该传给 net.Socket。
* 如果 autoClose 为 false，则即使出现错误，也不会关闭文件描述符。 应用程序负责关闭它并确保没有文件描述符泄漏。

### 13. fs.createWriteStream(path[, options])

* options.flags：写文件的方式。覆盖、追加或修改等。[可选择的值](http://nodejs.cn/api/fs.html#fs_file_system_flags)
