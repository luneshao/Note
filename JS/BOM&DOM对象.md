[原文链接](http://www.cnblogs.com/polk6/p/4957563.html)

# BOM对象

## window对象

### 方法

1.`atob(string base64Str)` ：将一个基于Base64编码的字符串解码为一个字符串。

2.`btoa(string str)` ：将一个字符串编码为一个Base64编码。

3.`scrollBy(long deltaWidth, long deltaHeight)` ：在当前滚动的基础上，横向滚动deltaWidth像素，纵向滚动deltaHeight像素。

## location对象

### 方法

1.`back()` ：当前所属窗口访问上一个访问过的URL。等同于浏览器的"后退"按钮，也等同于history.go(-1)。

2.`forward()` ：当前所属窗口访问下一个访问过的URL。等同于浏览器的"前进"按钮，也等同于history.go(1)。

3.`go(int index)` ：使当前窗口访问指定的访问过的URL。当前窗口访问过的URL，是存入一个数组。正数表示前进index个(点击"前进"按钮index次)，

负数表示后退index个(点击"后退"按钮index次)。

## location 对象

### 属性

1.`search` ：设置或返回当前页面URL的查询部分(从问号 (?) 开始的 URL)。

### 方法

1.`assign(string url)` ：设置当前页面加载指定的url，等同于设置href属性的值为url。

2.`reload()` ：重新加载当前页面的URL。可看成为刷新操作。

3.`replace(string url)` ：设置当前页面加载指定的url，并在浏览器历史记录中替换掉当前地址，进行"后退"操作不会显示当前访问过的记录。

# DOM 对象

## 方法

1.`ELElement querySelector(CssSelector)` ：获取该元素下第一个符合CssSelector的匹配子元素。若没有找到，返回null。

2.HTMLElement[] `querySelectorAll(CssSelector)` ：获取一个数组，包含该元素下所有符合CssSelector匹配的子元素。CssSelector规范参照上个方法的详解。

## event 对象

1.冒泡事件：当子元素触发某一事件时，父元素会触发相同时间(事件为允许冒泡)。

2.阻止后续处理程序：通过addEventListener()方法可以给元素的同一事件注册多个处理程序，在某个事件中调用了stopImmediatePropagation() 方法后，

后面已经注册的处理程序将不会执行。比如，某个元素在click事件上注册了3个函数，在第2个函数上调用了stopImmediatePropagation()方法，第3个函数不会执行。

### 属性

1.`bubbles` ：只读，获取此事件是否冒泡。

2.`cancelable` ：只读，获取此事件是否可被撤销。true：事件可撤销。可调用preventDefault()取消后续的默认动作。flase：事件不可撤销。

3.`currentTarget` ：只读，获取正在处理此事件的对象，可以为Element、Document对象等等。

4.`target` ：只读，获取触发此事件的对象。

5.`eventPhase` ：只读，表示事件的处理阶段：0表示没有正在处理，1表示捕获阶段，2表示目标阶段，3表示冒泡阶段。

### 方法

1.`preventDefault()` ：终止事件的后续默认操作(事件要可撤销，即cancelable属性为true)。如：checkbox的click事件，执行这代码，元素不会被勾选和取消勾选。

2.`stopImmediatePropagation()` ：阻止当前事件的冒泡行为并且阻止此元素上相同类型事件的后续处理函数。

3.`stopPropagation()` ：阻止当前事件的冒泡行为。

`currentTarget`与 `target` 属性的区别

`currentTarget` ：获取正在处理此事件的对象。

`target` ：获取触发此事件的对象。

