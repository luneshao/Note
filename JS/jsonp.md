# jsonp
[原文链接](https://www.cnblogs.com/chiangchou/p/jsonp.html)

intro: 

  `jsonp`发送的不是`ajax`请求，是动态创建一个`script`标签,`src`指向请求的地址, 地址后面有一个`callback = func` 参数,服务端检测url带一个参数，

返回`func ( result )`,相当于在前端执行 `func`方法。所以，使用前在要在前端注册`func`方法,result 就是返回的数据。
