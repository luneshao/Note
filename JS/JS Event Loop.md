# JS Event Loop

这里先占个坑

## 相关知识：

[vue2.6版本更新](https://mp.weixin.qq.com/s/ivP5oyvfKDkxam2PzYtnUg)

[了解task、microTask](https://www.cnblogs.com/dong-xu/p/7000139.html)

### `Macrotasks`和`Microtasks`

  因为看到`vue`的 让 `nextTick` 恢复使用 `Microtask`,去查了一下`Macrotasks`和`Microtasks`, 然后了解到了js的任务序列, 所以暂做记录。

`Macrotasks` 和 `Microtasks` 都属于上述的异步任务中的一种，他们分别有如下API：

* macrotasks: `setTimeout`, `setInterval`, `setImmediate`, `I/O`, `UI rendering`

* microtasks: `process.nextTick`, `Promise`, `MutationObserver`
