# JS事件
## 事件
### 事件处理属性
* `btn.onfocus`及`btn.onblur` — 颜色将于按钮被置于焦点或解除焦点时改变（尝试使用Tab移动至按钮上，然后再移开）。<br>
  这些通常用于显示有关如何在置于焦点时填写表单字段的信息，或者如果表单字段刚刚填入不正确的值，则显示错误消息。
* `btn.ondblclick` — 颜色将仅于按钮被双击时改变。
* `window.onkeypress`, `window.onkeydown`, `window.onkeyup` — 当按钮被按下时颜色会发生改变. keypress 指的是<br>
  通俗意义上的按下按钮 (按下并松开)当用户在键盘上按下某个键(不是所有的键都会,比如ctrl)以后会触发keypress事件,<br>
  而 keydown 和 keyup 指的是按键动作的一部分,分别指按下和松开. 注意如果你将<br>
  事件处理器添加到按钮本身，它将不会工作 — 我们只能将它添加到代表整个浏览器窗口的 window对象中。
* `btn.onmouseover` 和 `btn.onmouseout` — 颜色将会在鼠标移入按钮上方时发生改变, 或者当它从按钮移出时.

### addEventListener()和removeEventListener()
  [原文](https://developer.mozilla.org/zh-CN/docs/Web/API/EventTarget/addEventListener)
  `addEventListener()`和`removeEventListener()`:这个机制带来了一些相较于旧方式的优点。有一个相对应的方法，removeEventListener()，<br>
  这个方法移除事件监听器。您也可以给同一个监听器注册多个处理器。
```javascript
  var btn = document.querySelector('button');

  function bgChange() {
    var rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
    document.body.style.backgroundColor = rndCol;
  }   

  btn.addEventListener('click', bgChange);
```
#### 语法:
  ```javascript
  target.addEventListener(type, listener, options);
  target.addEventListener(type, listener ,{capture: Boolean, passive: Boolean, once: Boolean});
  target.addEventListener(type, listener, useCapture);
  ```
  `type` - 表示监听事件类型的字符串。
  `listener` - 当所监听的事件类型触发时，会接收到一个事件通知（实现了 Event 接口的对象）对象。<br>
  `listener` 必须是一个实现了 `EventListener` 接口的对象，或者是一个`函数`。
  `options`:
  `capture`:  `Boolean`，表示 `listener` 会在该类型的`事件捕获阶段`传播到该 `EventTarget` 时触发。
  `once`:  `Boolean`，表示 `listener` 在添加之后`最多只调用一次`。如果是 `true`， `listener` 会在其被调用之后自动移除。
  `passive`: `Boolean`，表示 `listener` 永远不会调用 `preventDefault()`。如果 `listener` 仍然调用了这个函数，<br>
  客户端将会忽略它并抛出一个控制台警告。
  
#### 处理过程中`this`值的问题
  通常来说this的值是触发事件的元素的引用，这种特性在多个相似的元素使用同一个通用事件监听器时非常让人满意。
  当使用 addEventListener() 为一个元素注册事件的时候，句柄里的 this 值是该元素的引用。<br>
  其与传递给句柄的 event 参数的 currentTarget 属性的值一样。
  
### 事件对象
  有时候在事件处理函数内部，您可能会看到一个固定指定名称的参数，例如event，evt或简单的e。<br>
  这被称为事件对象，它被自动传递给事件处理函数，以提供额外的功能和信息。
```javascript
  function bgChange(e) {
  var rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
  e.target.style.backgroundColor = rndCol;
  console.log(e);
}  

btn.addEventListener('click', bgChange);
```
在这里，您可以看到我们在函数中包括一个事件对象，`e`，并在函数中设置背景颜色样式在`e.target上` - 它指的是`按钮本身`。<br>
事件对象` e `的`target`属性始终是事件刚刚发生的元素的引用。
  * `preventDefault()`:组织默认行为。
  * 事件冒泡及捕获
  当一个事件发生在具有父元素的元素上时，现代浏览器运行两个不同的阶段 - 捕获阶段和冒泡阶段。
#### 捕获阶段
    * 浏览器检查元素的最外层祖先`<html>`，是否在捕获阶段中注册了一个`onclick`事件处理程序，如果是，则运行它。
    * 然后，它移动到`<html>`中的下一个元素，并`执行相同`的操作，然后是下一个元素，依此类推，直到到达实际点击的元素。
#### 在冒泡阶段，恰恰相反:
    * 浏览器检查实际点击的元素是否在冒泡阶段中注册了一个onclick事件处理程序，如果是，则运行它
    * 然后它移动到下一个直接的祖先元素，并做同样的事情，然后是下一个，等等，直到它到达<html>元素。
    在现代浏览器中，默认情况下，所有事件处理程序都在冒泡阶段进行注册。
    `用stopPropagation()修复问题`
    标准事件对象具有可用的名为 `stopPropagation()`的函数, 当在事件对象上调用该函数时，它只会让当前事件处理程序运行，<br>
    但事件不会在冒泡链上进一步扩大，因此将不会有更多事件处理器被运行(不会向上冒泡)。
    ```javascript
    video.onclick = function(e) {
    e.stopPropagation();
    video.play();
    };
    ```
  * 事件委托
  冒泡还允许我们利用事件委托——这个概念依赖于这样一个事实,如果你想要在大量子元素中单击任何一个都可以运行一段代码，您可以将事件监听器设置在其父节点上，<br>
  并将事件监听器气泡的影响设置为每个子节点，而不是每个子节点单独设置事件监听器。
  

`注意`:一开始，您不应该混用 HTML 和 JavaScript，因为这样文档很难解析——最好的办法是只在一块地方写 JavaScript 代码。
