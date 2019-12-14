# 跨域

```
涉及面试题：什么是跨域？为什么浏览器要使用同源策略？你有几种方式可以解决跨域问题？了解预检请求嘛？
```

## 一、什么是跨域

* 广义上跨域
* 狭义上跨域 => 跨域一般指的是这个

### 同源策略

因为浏览器出于安全考虑，有同源策略。也就是说，如果`协议`、`域名`或者`端口`有一个不同就是跨域，Ajax 请求会失败

* cookie
* localStorage
* sessionStorage

#### 那么是出于什么安全考虑才会引入这种机制呢？

其实主要是用来防止 CSRF 攻击的。简单点说，CSRF 攻击是利用用户的登录态发起恶意请求

#### 然后我们来考虑一个问题，请求跨域了，那么请求到底发出去没有？

请求必然是发出去了，但是浏览器拦截了响应。你可能会疑问明明通过表单的方式可以发起跨域请求，为什么 Ajax 就不会。因为归根结底，`跨域是为了阻止用户读取到另一个域名下的内容`，Ajax 可以获取响应，浏览器认为这不安全，所以拦截了响应。但是表单并不会获取新的内容，所以可以发起跨域请求。同时也说明了跨域并不能完全阻止 CSRF，因为请求毕竟是发出去了

## 二、跨域解决方案

1. JSONP
2. CORS
3. Node中间件
4. Nginx代理
5. websocket
6. postMessage
7. document.domain => iframe
8. location.hash => iframe
9. window.name => iframe

### 1、JSONP

JSONP 的原理很简单，就是利用 <script> 标签没有跨域限制的漏洞。通过 <script> 标签指向一个需要访问的地址并提供一个回调函数来接收数据当需要通讯时
  
* 只限于get
* 默认不能使用cookie

自己封装的JSONP

```
function jsonp(url, jsonpCallback, success) {
  let script = document.createElement('script')
  script.src = url
  script.async = true
  script.type = 'text/javascript'
  window[jsonpCallback] = function(data) {
    success && success(data)
  }
  document.body.appendChild(script)
}
jsonp('http://xxx', 'callback', function(value) {
  console.log(value)
})
```

### CORS

* Access-Control-Allow-Origin
* Access-Control-Allow-Methods
* Access-Control-Allow-Headers
* Access-Control-Allow-Credentials
* 简单请求和复杂请求 => option，通过该请求来知道服务端是否允许跨域请求

### postMessage

这种方式通常用于获取嵌入页面中的第三方页面数据。一个页面发送消息，另一个页面判断来源并接收消息

### document.domain
