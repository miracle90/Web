# Event Loop

## 进程与线程

相信大家经常会听到 JS 是单线程执行的，但是你是否疑惑过什么是线程？

讲到线程，那么肯定也得说一下进程。本质上来说，两个名词都是 CPU 工作时间片的一个描述。

进程描述了 CPU 在运行指令及加载和保存上下文所需的时间，放在应用上来说就代表了一个程序。线程是进程中的更小单位，描述了执行一段指令所需的时间。

把这些概念拿到浏览器中来说，当你打开一个 Tab 页时，其实就是创建了一个进程，一个进程中可以有多个线程，比如渲染线程、JS 引擎线程、HTTP 请求线程等等。当你发起一个请求时，其实就是创建了一个线程，当请求结束后，该线程可能就会被销毁。

上文说到了 JS 引擎线程和渲染线程，大家应该都知道，在 JS 运行的时候可能会阻止 UI 渲染，这说明了两个线程是互斥的。这其中的原因是因为 JS 可以修改 DOM，如果在 JS 执行的时候 UI 线程还在工作，就可能导致不能安全的渲染 UI。这其实也是一个单线程的好处，得益于 JS 是单线程运行的，可以达到节省内存，节约上下文切换时间，没有锁的问题的好处。当然前面两点在服务端中更容易体现，对于锁的问题，形象的来说就是当我读取一个数字 15 的时候，同时有两个操作对数字进行了加减，这时候结果就出现了错误。解决这个问题也不难，只需要在读取的时候加锁，直到读取完毕之前都不能进行写入操作。

## 执行栈

可以把执行栈认为是一个存储函数调用的栈结构，遵循先进后出的原则。

## 浏览器中的Event Loop

![](https://user-gold-cdn.xitu.io/2018/11/23/16740fa4cd9c6937?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

* 首先执行同步代码，这属于宏任务
* 当执行完所有同步代码后，执行栈为空，查询是否有异步代码需要执行
* 执行所有微任务
* 当执行完所有微任务后，如有必要会渲染页面
* 然后开始下一轮 Event Loop，执行宏任务中的异步代码，也就是 setTimeout 中的回调函数

### 微任务包括

* process.nextTick
* promise
* MutationObserver

### 宏任务

* script
* setTimeout
* setInterval
* setImmediate
* I/O
* UI rendering

## Node中的Event Loop

![](https://user-gold-cdn.xitu.io/2018/11/13/1670c3fe3f9a5e2b?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

### 三大关键阶段

首先，梳理一下 nodejs 三个非常重要的执行阶段:


1. 执行 定时器回调 的阶段。检查定时器，如果到了时间，就执行回调。这些定时器就是setTimeout、setInterval。这个阶段暂且叫它timer。


2. 轮询(英文叫poll)阶段。因为在node代码中难免会有异步操作，比如文件I/O，网络I/O等等，那么当这些异步操作做完了，就会来通知JS主线程，怎么通知呢？就是通过'data'、'connect'等事件使得事件循环到达 poll 阶段。到达了这个阶段后:


如果当前已经存在定时器，而且有定时器到时间了，拿出来执行，eventLoop 将回到timer阶段。

如果没有定时器, 会去看回调函数队列。

* 如果队列不为空，拿出队列中的方法依次执行
* 如果队列为空，检查是否有 setImmdiate 的回调

有则前往check阶段(下面会说)

没有则继续等待，相当于阻塞了一段时间(阻塞时间是有上限的), 等待 callback 函数加入队列，加入后会立刻执行。一段时间后自动进入 check 阶段。

3. check 阶段。这是一个比较简单的阶段，直接执行 setImmdiate 的回调。

### process.nextTick

这个函数其实是独立于 Event Loop 之外的，它有一个自己的队列，当每个阶段完成后，如果存在 nextTick 队列，就会清空队列中的所有回调函数，并且优先于其他 microtask 执行。

```
setTimeout(() => {
 console.log('timer1')

 Promise.resolve().then(function() {
   console.log('promise1')
 })
}, 0)

process.nextTick(() => {
 console.log('nextTick')
 process.nextTick(() => {
   console.log('nextTick')
   process.nextTick(() => {
     console.log('nextTick')
     process.nextTick(() => {
       console.log('nextTick')
     })
   })
 })
})
```

