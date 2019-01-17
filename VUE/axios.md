#  axios

## API

### 可以通过向 axios 传递相关配置来创建请求

* axios(config)

为方便起见，为所有支持的请求方法提供了别名

* axios.request(config)

* axios.get(url[, config])

* axios.delete(url[, config])

* axios.head(url[, config])

* axios.post(url[, data[, config]])

* axios.put(url[, data[, config]])

* axios.patch(url[, data[, config]])

在使用别名方法时， url、method、data 这些属性都不必在配置中指定。

### 可以使用自定义配置新建一个 axios 实例

axios.create([config])

以下是可用的实例方法。指定的配置将与实例的配置合并

axios#request(config) ... etc

## 请求配置

这些是创建请求时可以用的配置选项。只有 url 是必需的。如果没有指定 method，请求将默认使用 get 方法。

## 拦截器

在请求或响应被 then 或 catch 处理前拦截它们。

## 取消

使用 cancel token 取消请求

## Features

* 从浏览器中创建 `XMLHttpRequests`

* 从 node.js 创建 [http](https://nodejs.org/api/http.html) 请求

* 支持 [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) API

* 拦截请求和响应

* 转换请求数据和响应数据

* 取消请求

* 自动转换 JSON 数据

* 客户端支持防御 XSRF

### tip: vue试用axios发送post请求，服务端收不到参数

[原文链接](https://blog.csdn.net/csdn_yudong/article/details/79668655)

问题复现

```javascript
 axios({
  method: 'post',
  url: '/apis/news/getNewsList',
  data: {
    type: 2,
    num: 5,
    page: 1,
    index: true,
    last: false
  }
})
  .then(res => {
    resolve(res)
  })
```

原因：

我们的 Content-Type 变成了 application/json;charset=utf-8

然后，因为我们的参数是 JSON 对象，axios 帮我们做了一个 stringify 的处理。

而且查阅 axios 文档可以知道：axios 使用 post 发送数据时，默认是直接把 json 放到请求体中提交到后端的。

那么，这就与我们服务端要求的 'Content-Type': 'application/x-www-form-urlencoded' 以及 @RequestParam 不符合。

解决办法：

```javascript
  let param = new URLSearchParams()

  for (let i in params) {
    param.append(i, params[i])
  }
  
  let instance = axios.create({
    timeout: 1000,
    headers: {
      'Content-Type': 'application/x-www-form-urlencoded'
    }
  })

  instance.post('/apis/news/getNewsList', param)
    .then(res => {
      resolve(res)
    })
```
