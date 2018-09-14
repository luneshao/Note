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
