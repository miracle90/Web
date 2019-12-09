# Front End

web开发技术栈大全

## :dart: 浏览器

### 常见面试题

* 页面白屏的原因和解决方法

### [1、事件机制](https://github.com/miracle90/Web/blob/master/docs/browser/event.md)

* 注册事件
* 事件冒泡
* 事件捕获
* 事件代理

### [2、跨域](https://github.com/miracle90/Web/blob/master/docs/browser/cross-domain.md)

* 什么是跨域
* 浏览器同源策略
* 跨域解决方案

### [3、存储](https://github.com/miracle90/Web/blob/master/docs/browser/storage.md)

* cookie
* localStorage
* sessionStorage
* indexDB
* Service Worker

### [4、浏览器缓存](https://github.com/miracle90/Web/blob/master/docs/browser/cache.md)

* Service Worker
* mermory cache
* Disk cache
* Push cache
* 强缓存 Expires Cache-control
* 协商缓存 Last-modified、If-Modified-Since、ETag、If-None-Match

### [5、浏览器渲染原理](https://github.com/miracle90/Web/blob/master/docs/browser/render.md)

* 浏览器接收到 HTML 文件并转换为 DOM 树
* 将 CSS 文件转换为 CSSOM 树
* 当我们生成 DOM 树和 CSSOM 树以后，就需要将这两棵树组合为渲染树
* 根据渲染树来进行布局（也可以叫做回流）

## :dart: [web安全](https://github.com/miracle90/Web/blob/master/docs/security/web-security.md)

* XSS
* CSRF
* 点击劫持
* SQL注入
* DNS攻击

## :dart: [前端监控](https://github.com/miracle90/Web/blob/master/docs/monitoring/monitoring.md)

* 页面埋点
* 性能监控
* 异常监控

## :dart: [网络相关](https://github.com/miracle90/Web/blob/master/docs/network/network.md)

* OSI七层网络协议（Open System Interconnection）
* 应用层
* 表示层
* 会话层
* 传输层
* 网络层
* 数据链路层
* 物理层
* http/https
* http1.1/http2.0
* tcp与udp
* ip
* 3次握手，4次挥手
* 常见状态码
* get/post
* 抓包
* websocket

### 常见面试题

* content-type的四种类型
* input file上传的内容是什么
* ajax可以上传file吗，怎么传
* form表单提交和json提交的内容一样吗
* http协议中缓存的状态码是多少？重定向的状态码是多少？301和302的区别？永久重定向和暂时重定向的区别？
* websocket如果连接异常，有降级处理方案吗？答心跳轮询。请求提示，说长轮询。

## :dart: [设计模式](https://github.com/miracle90/Web/blob/master/docs/design-patterns/design-patterns.md)

* 面向对象
* SOLID五大设计原则
* 单例模式
* 工厂模式
* 发布订阅模式/观察者模式
* 代理模式
* 装饰器模式
* 发布订阅模式和观察者模式的异同以及实际应用
* 可以说出几种设计模式在开发中的实际应用，理解框架源码中对设计模式的应用

## :dart: 前端新技术

### PWA
### Flutter
### 了解WebWorker吗？一般使用WebWorker解决什么问题？

## Html

* iframe的缺点

## Js

* 1、原始类型有哪几种？null 是对象嘛？
* 2、0.1 + 0.2 ！= 0.3
* 3、typeof 是否能正确判断类型？instanceof 能正确判断对象的原理是什么？
* 4、== 和 === 有什么区别？
* 5、[] == ![]
* 6、闭包
* 7、什么是浅拷贝？如何实现浅拷贝？什么是深拷贝？如何实现深拷贝？
* 8、如何理解原型？如何理解原型链？

* 原型
* 闭包
* JavaScript事件模型
* 事件代理
* this
* 0.1 + 0.2 ！= 0.3
* null和undefined的区别
* ['1', '2', '3'].map(parseInt)的输出结果是什么？
* ['1', '2', '3'].fliter(parseInt)的输出结果是什么？
* 说出几种数组去重的方式
* 深拷贝和浅拷贝吗
* 手动实现一个bind方法
* （React）实现一个防抖的模糊查询输入框
*  手动封装一个请求函数，可以设置最大请求次数，请求成功则不再请求，请求失败则继续请求直到超过最大次数
* JS中==和===的区别
* 实现函数柯里化
* 跨标签页的通讯方式有哪些
* 实现一个函数判断数据类型
* sessionStorage、localStorage的区别
* cookie的大小
* 类型判断
* 宿主对象和原生对象
* 隐性转换
* 断网情况下怎样实现页面离线编辑？除了localStorage和sessionStorage之外，还有什么缓存方式？（请求提示，说indexDB）

#### Jquery

* jquery一个对象绑定多个事件怎么实现的
* jquery的bing、delege、live的区别
* jquery数组转成json怎么实现的

#### Typescript

#### Es6

* 1、什么是提升？什么是暂时性死区？var、let 及 const 区别？
* 2、原型如何实现继承？Class 如何实现继承？Class 本质是什么？
* 3、涉及面试题：Proxy 可以实现什么功能？
* 4、并发与并行的区别？
* ES6的新特性有哪些？

#### Babel

#### 异步

* 聊聊promise async/await
* Promise/A+规范
* 手动实现Promise，写出伪代码
* async 函数与 Generator 与co模块
* 如果Promise代码执行出错，setTimeout中的方法是否还会继续执行？为什么？

#### 进程和线程

## Css~

* 盒模型
* 选择器优先级（!important > 行内样式 > id选择器 > class选择器 > 标签选择器 > * > 继承 > 默认）
* CSS3中transition和animation的属性分别有哪些
* Web动画的实现方法
* 用transform和left实现动画的区别
* 如何开启GPU加速？
* 重绘和重排的区别

#### Flex布局

* 说出space-between和space-around的区别？

## 框架~

* 虚拟DOM
* vue和react的区别；单项数据流的优势
* mvvm怎么实现双向绑定的
* 你会用的几种框架以及区别

#### Vue

* vue中8种组件通信方式

#### React

* 虚拟树原理
* 组件间通信
* 如何实现双向绑定
* React实现的移动应用中，如果出现卡顿，有哪些可以考虑的优化方案
* 什么是高阶组件(HOC)
* 说说对React Hooks的理解
* Redux的理解
* React为什么要使用虚拟DOM？
* React事件绑定机制

## Node~

* Koa
* Express
* Egg.js
* queryParams方法

## 构建工具~

#### Webpack

* webpack都需要配置那些内容

## 微信小程序~

## 前端性能优化~

* 性能分析，怎么量化的分析一个页面的性能
* 你所知道的前端性能优化方案

## 兼容性、适配问题~

* 移动端300ms延迟

## 算法~

* 如何从10000个数中找到最大的10个数
* 数组排序
* 从数组中取出几个最小的值

## Nginx~

* web 服务器的理解

## Linux~

## Docker~

## 数据库~

#### MySQL

#### Mongodb

#### Redis

## 项目相关~

* 项目中的亮点、难点
* 聊一个你印象最深刻的项目经历
* 项目做了什么事情
* 用到什么技术
* 碰到什么困难，用了什么方法改进
* 最终达到怎样的效果

## 前端团队建设~

* 项目搭建
* 版本管理
* 公共组件库
* 代码规范
