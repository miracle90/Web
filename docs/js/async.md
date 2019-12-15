# js异步发展流程

## 并行与并发

* 并发是宏观概念，我分别有任务 A 和任务 B，在一段时间内通过任务间的切换完成了这两个任务，这种情况就可以称之为并发。
* 并行是微观概念，假设 CPU 中存在两个核心，那么我就可以同时完成任务 A、B。同时完成多个任务的情况就可以称之为并行。

## 回调函数（Callback）

`回调地狱（Callback hell）`

### 缺点

* 嵌套函数存在耦合性，一旦有所改动，就会牵一发而动全身
* 嵌套函数一多，就很难处理错误
* 不能使用 try catch 捕获错误
* 不能直接 return

## Promise

Promise 翻译过来就是承诺的意思，这个承诺会在未来有一个确切的答复，并且该承诺有三种状态，分别是：

* 等待中（pending）
* 完成了 （resolved）
* 拒绝了（rejected）

这个承诺一旦从等待状态变成为其他状态就永远不能更改状态了，也就是说一旦状态变为 resolved 后，就不能再次改变

```
new Promise((resolve, reject) => {
  resolve('success')
  // 无效
  reject('reject')
})
```

### 优点

* Promise 实现了链式调用
* Promise 也很好地解决了回调地狱的问题

### 缺点

* 比如无法取消 Promise
* 错误需要通过回调函数捕获。

## Generator

Generator 函数调用和普通函数不同，它会返回一个迭代器

```
function *foo(x) {
  let y = 2 * (yield (x + 1))
  let z = yield (y / 3)
  return (x + y + z)
}
let it = foo(5)
console.log(it.next())   // => {value: 6, done: false}
console.log(it.next(12)) // => {value: 8, done: false}
console.log(it.next(13)) // => {value: 42, done: true}
```

## async、await

一个函数如果加上 async ，那么该函数就会返回一个 Promise

```
async function test() {
  return "1"
}
console.log(test()) // -> Promise {<resolved>: "1"}
```

async 就是将函数返回值使用 Promise.resolve() 包裹了下，和 then 中处理返回值一样，并且 await 只能配套 async 使用

await 就是 generator 加上 Promise 的语法糖，且内部实现了自动执行 generator。如果你熟悉 co 的话，其实自己就可以实现这样的语法糖。

### 优点

* 优势在于处理 then 的调用链，能够更清晰准确的写出代码，毕竟写一大堆 then 也很恶心
* 并且也能优雅地解决回调地狱问题

### 缺点

因为 await 将异步代码改造成了同步代码，如果多个异步代码没有依赖性却使用了 await 会导致性能上的降低。

## 常用定时器函数

setTimeout、setInterval、requestAnimationFrame
