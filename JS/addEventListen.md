# EventTarget.addEventListener()

格式: 
```javascript
target.addEventListener(type, listener, options);
```

'type': 表示监听事件类型的字符串。

'listener': 当所监听的事件类型触发时，会接收到一个事件通知（实现了 Event 接口的对象）对象。

listener 必须是一个实现了 EventListener 接口的对象，或者是一个函数。

'options': 

*'capture':  Boolean，表示 listener 会在该类型的事件捕获阶段传播到该 EventTarget 时触发。

*'once':  Boolean，表示 listener 在添加之后最多只调用一次。如果是 true， listener 会在其被调用之后自动移除。

*'passive': Boolean，表示 listener 永远不会调用 preventDefault()。如果 listener 仍然调用了这个函数，客户端将会忽略它并抛出一个控制台警告。

