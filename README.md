# Front End

web开发知识库

## 一、Javascript

### 1、基础知识点

* [闭包](https://github.com/miracle90/Web/blob/master/docs/js/closure.md)
* [原型](https://github.com/miracle90/Web/blob/master/docs/js/prototype.md)
* [this、call、apply、bind + 手写](https://github.com/miracle90/Web/blob/master/docs/js/this-call-apply-bind.md)
* [new](https://github.com/miracle90/Web/blob/master/docs/js/new.md)
* [typeof、instanceof](https://github.com/miracle90/Web/blob/master/docs/js/typeof-instanceof.md)
* [深浅拷贝](https://github.com/miracle90/Web/blob/master/docs/js/clone.md)
* [节流、防抖](https://github.com/miracle90/Web/blob/master/docs/js/throttle-debounce.md)
* [垃圾回收机制](https://github.com/miracle90/Web/blob/master/docs/js/gc.md)
* [柯里化](https://github.com/miracle90/Web/blob/master/docs/js/curry.md)
* [数组去重、排序、扁平化](https://github.com/miracle90/Web/blob/master/docs/js/arry-solve.md)

### [2、异步](https://github.com/miracle90/Web/blob/master/docs/js/async.md)

* 并发与并行
* 回调、promise、generator、async（Generator 与co模块）
* Promise/A+规范
* [手写promise](https://github.com/miracle90/Web/blob/master/docs/js/promise.js)

### [2、Event Loop](https://github.com/miracle90/Web/blob/master/docs/js/event-loop.md)

* 浏览器中的Event Loop
* Node中的Event Loop

### 3、Es6

* es6常用特性
* 1、什么是提升？什么是暂时性死区？var、let 及 const 区别？
* 2、原型如何实现继承？Class 如何实现继承？Class 本质是什么？
* 3、涉及面试题：Proxy 可以实现什么功能？

### [3、Babel](https://github.com/miracle90/Web/blob/master/docs/js/babel.md)

### 4、Jquery

* jquery一个对象绑定多个事件怎么实现的
* jquery的bing、delege、live的区别
* jquery数组转成json怎么实现的

### 其他专题

* Typescript

### [常见面试题](https://github.com/miracle90/Web/blob/master/docs/js/questions.md)

* 1、0.1 + 0.2 ！= 0.3
* 2、== 和 === 有什么区别？
* 3、[] == ![]

### 其他面试题

* JavaScript事件模型
* null和undefined的区别
* ['1', '2', '3'].map(parseInt)的输出结果是什么？
* ['1', '2', '3'].fliter(parseInt)的输出结果是什么？
* （React）实现一个防抖的模糊查询输入框
*  手动封装一个请求函数，可以设置最大请求次数，请求成功则不再请求，请求失败则继续请求直到超过最大次数
* 跨标签页的通讯方式有哪些
* 实现一个函数判断数据类型
* 类型判断
* 宿主对象和原生对象
* 隐性转换
* 断网情况下怎样实现页面离线编辑？除了localStorage和sessionStorage之外，还有什么缓存方式？（请求提示，说indexDB）

## 二、Css

* 1、Flex布局

* 2、盒模型

* 3、BFC

* 4、淘宝flexible解决方案的原理

* 5、移动端1px

* 6、transform比top性能好的原因

### 常见面试题

* 说出space-between和space-around的区别？
* 选择器优先级（!important > 行内样式 > id选择器 > class选择器 > 标签选择器 > * > 继承 > 默认）
* CSS3中transition和animation的属性分别有哪些
* Web动画的实现方法
* 用transform和left实现动画的区别
* 如何开启GPU加速？
* 重绘和重排的区别

## 三、Vue

* 1、双向数据绑定原理
* 2、虚拟DOM
* [3、patch阶段的diff算法](https://github.com/miracle90/Web/blob/master/docs/vue/diff.md)
* 4、vue-router原理
* 5、vuex原理
* 6、nextTick原理
* 7、Object.defineProperty弊端
* 8、Vue3.0
* 9、对比vue和react
* [10、vue-ssr](https://github.com/miracle90/Web/blob/master/docs/vue/ssr.md)

### 常见面试题

* computed和watch区别
* 组件间通信方式
* 生命周期
* 单项数据流的优势
* mvvm怎么实现双向绑定的

## 四、React

* 生命周期

### 其他

* 虚拟树原理
* 组件间通信
* 如何实现双向绑定
* React实现的移动应用中，如果出现卡顿，有哪些可以考虑的优化方案
* 什么是高阶组件(HOC)
* 说说对React Hooks的理解
* Redux的理解
* React为什么要使用虚拟DOM？
* React事件绑定机制

## 五、Webpack

* [打包机制](https://github.com/miracle90/Web/blob/master/docs/webpack/pack.md)

### [常用配置](https://github.com/miracle90/Web/blob/master/docs/webpack/config.md)

### [性能优化](https://github.com/miracle90/Web/blob/master/docs/webpack/optimize.md)

### [源码分析](https://github.com/miracle90/Web/blob/master/docs/webpack/resource.md)

## 六、网络相关

### [1、CDN](https://github.com/miracle90/Web/blob/master/docs/network/cdn.md)
### [2、DNS解析](https://github.com/miracle90/Web/blob/master/docs/network/dns.md)
### [3、UDP和TCP](https://github.com/miracle90/Web/blob/master/docs/network/tcp-udp.md)
### [4、HTTP和HTTPS](https://github.com/miracle90/Web/blob/master/docs/network/http-https.md)
### [5、HTTP/1和HTTP/2](https://github.com/miracle90/Web/blob/master/docs/network/http2.md)
### 6、websocket
### 其他

* ip
* 3次握手，4次挥手
* 常见状态码
* get/post
* 抓包

### 常见面试题

* content-type的四种类型
* input file上传的内容是什么
* ajax可以上传file吗，怎么传
* form表单提交和json提交的内容一样吗
* http协议中缓存的状态码是多少？重定向的状态码是多少？301和302的区别？永久重定向和暂时重定向的区别？
* websocket如果连接异常，有降级处理方案吗？答心跳轮询。请求提示，说长轮询

## 七、浏览器

### [1、事件机制](https://github.com/miracle90/Web/blob/master/docs/browser/event.md)
### [2、跨域](https://github.com/miracle90/Web/blob/master/docs/browser/cross-domain.md)
### [3、本地存储](https://github.com/miracle90/Web/blob/master/docs/browser/storage.md)

* cookie、session
* localStorage、sessionStorage
* indexDB

### [4、浏览器缓存](https://github.com/miracle90/Web/blob/master/docs/browser/cache.md)

* 强缓存 Expires Cache-control
* 协商缓存 Last-modified、If-Modified-Since、ETag、If-None-Match
* Service Worker
* mermory cache
* Disk cache
* Push cache

### [5、浏览器渲染原理](https://github.com/miracle90/Web/blob/master/docs/browser/render.md)

### 6、进程和线程

### 其他

* web worker

### 常见面试题

* 页面白屏的原因和解决方法

## [八、web安全](https://github.com/miracle90/Web/blob/master/docs/security/web-security.md)

* XSS
* CSRF
* 点击劫持
* SQL注入
* DNS攻击

## [九、前端监控](https://github.com/miracle90/Web/blob/master/docs/monitoring/monitoring.md)

* 页面埋点
* 性能监控
* 异常监控

## [十、设计模式](https://github.com/miracle90/Web/blob/master/docs/design-patterns/design-patterns.md)

* 面向对象
* SOLID五大设计原则
* 单例模式
* 工厂模式
* 发布订阅模式/观察者模式
* 代理模式
* 装饰器模式
* 发布订阅模式和观察者模式的异同以及实际应用
* 可以说出几种设计模式在开发中的实际应用，理解框架源码中对设计模式的应用

## [十一、数据结构和算法](https://github.com/miracle90/Web/blob/master/docs/data-structure/data-structure.md)

* 时间复杂度
* 栈
* 队列
* 链表
* 树
* AVL 树
* Trie
* 并查集
* 堆
* 位运算
* 排序
* 动态规划

### 常见面试题

* 如何从10000个数中找到最大的10个数
* 数组排序
* 从数组中取出几个最小的值

## [十二、微信小程序](https://github.com/miracle90/Web/blob/master/docs/wxApp/wxApp.md)

* 生命周期
* 底层原理
* 性能优化
* 常见问题

## Html

* iframe的缺点

## Node

* Koa
* Express
* Egg.js
* queryParams方法

## 前端性能优化

* 性能分析，怎么量化的分析一个页面的性能
* 你所知道的前端性能优化方案

## 兼容性、适配问题

* 移动端300ms延迟

## 开发性问题

* [浏览器指纹](https://github.com/miracle90/Web/blob/master/docs/fe/fingerprint.md)
* 最近在研究什么技术
* 项目中的亮点、难点
* 聊一个你印象最深刻的项目经历
* 项目做了什么事情
* 用到什么技术
* 碰到什么困难，用了什么方法改进
* 最终达到怎样的效果

## 前端团队建设

* 项目搭建
* 版本管理
* 公共组件库
* 代码规范

## 前端工程化

* 持续集成
* 自动化测试
* webpack
* jekins

## 前端新技术

### PWA
### Flutter
### 了解WebWorker吗？一般使用WebWorker解决什么问题？

## Nginx

* web 服务器的理解

## Linux

## Docker

## 数据库

#### MySQL

#### Mongodb

#### Redis
