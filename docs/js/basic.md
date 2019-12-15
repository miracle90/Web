# Javascript基础知识点

## 一、this/apply/call/bind + 手写

在函数执行时，this 总是指向调用该函数的对象

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

## 二、new

`new 的原理是什么？通过 new 的方式创建对象和通过字面量创建有什么区别？`

在调用 new 的过程中会发生以上四件事情：

1. 新生成了一个对象
2. 链接到原型
3. 绑定 this
4. 返回新对象

根据以上几个过程，我们也可以试着来自己实现一个 new

```
function create() {
  // 创建一个空对象
  let obj = {}
  // 获取构造函数
  let Con = [].shift.call(arguments)
  // 设置空对象的原型
  obj.__proto__ = Con.prototype
  // 绑定 this 并执行构造函数
  let result = Con.apply(obj, arguments)
  // 确保返回值为对象
  return result instanceof Object ? result : obj
}
```

对于创建一个对象来说，更推荐使用字面量的方式创建对象（无论性能上还是可读性）。因为你使用 new Object() 的方式创建对象需要通过作用域链一层层找到 Object，但是你使用字面量的方式就没这个问题。

## 三、typeof、instanceof

`typeof的原理是什么？instanceof的原理是什么？`

### typeof

js 在底层存储变量的时候，会在变量的机器码的低位1-3位存储其类型信息

* 000：对象
* 010：浮点数
* 100：字符串
* 110：布尔
* 1：整数

`null：所有机器码均为0，所以 typeof null // 'object'`

typeof 对于原始类型来说，除了 null 都可以显示正确的类型

```
typeof 1 // 'number'
typeof '1' // 'string'
typeof undefined // 'undefined'
typeof true // 'boolean'
typeof Symbol() // 'symbol'
```

typeof 对于对象来说，除了函数都会显示 object，所以说 typeof 并不能准确判断变量到底是什么类型

```
typeof [] // 'object'
typeof {} // 'object'
typeof console.log // 'function'
```

### instanceof

instanceof 可以正确的判断对象的类型，因为内部机制是通过判断对象的原型链中是不是能找到类型的 prototype。

我们也可以试着实现一下 instanceof

```
function myInstanceof(left, right) {
  // 右值的prototype
  let prototype = right.prototype
  // 左值的__proto__
  left = left.__proto__
  while (true) {
    // 一直循环判断对象的原型是否等于类型的原型，直到对象原型为 null，因为原型链最终为 null
    if (left === null || left === undefined)
      return false
    if (prototype === left)
      return true
    left = left.__proto__
  }
}
```

### 类型判断 => Object.prototype.toString.call

```
Object.prototype.toString.call(1) // "[object Number]"

Object.prototype.toString.call('hi') // "[object String]"

Object.prototype.toString.call({a:'hi'}) // "[object Object]"

Object.prototype.toString.call([1,'a']) // "[object Array]"

Object.prototype.toString.call(true) // "[object Boolean]"

Object.prototype.toString.call(() => {}) // "[object Function]"

Object.prototype.toString.call(null) // "[object Null]"

Object.prototype.toString.call(undefined) // "[object Undefined]"

Object.prototype.toString.call(Symbol(1)) // "[object Symbol]"
```

## 三、深浅拷贝


* 节流、防抖
* 柯里化
* 垃圾回收机制
