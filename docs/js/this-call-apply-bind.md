# this/apply/call/bind + 手写

### 在函数执行时，this 总是指向调用该函数的对象

`可以从上述代码中发现，不管我们给函数 bind 几次，fn 中的 this 永远由第一次 bind 决定`

### 手写 call、apply 及 bind 函数

```
// call => 参数作为函数的第二个参数及之后依次传入
Function.prototype.myCall = function (context) {
  if (typeof this !== 'function') {
    throw new TypeError('Error')
  }
  context = context || window
  context.fn = this

  const args = [...arguments].slice(1)
  const result = context.fn(args)

  delete context.fn
  return result
}

// apply => 参数作为函数的第二个参数传入
Function.prototype.myApply = function (context) {
  if (typeof this !== 'function') {
    throw new TypeError('Error')
  }
  context = context || window
  context.fn = this

  let result

  // 判断是否传入参数
  if (arguments[1]) {
    result = context.fn(...arguments[1])
  } else {
    result = context.fn()
  }

  delete context.fn
  return result
}

// bind
Function.prototype.myBind = function (context) {
  if (typeof this !== 'function') throw new TypeError('Error')

  // 方法
  const self = this
  const args = [...arguments].slice(1)

  return function F() {
    // 因为返回了一个函数，我们可以 new F()，所以需要判断
    if (this instanceof F) {
      // 对于 new 的情况来说，不会被任何方式改变 this，所以对于这种情况我们需要忽略传入的 this
      return new self(...args, ...arguments)
    }
    // 拼接参数
    return self.apply(context, args.concat(...arguments))
  }
}

```
