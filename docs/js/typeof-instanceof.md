# typeof、instanceof + 类型判断

`typeof的原理是什么？instanceof的原理是什么？`

### 1、typeof

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

### 2、instanceof

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

### 3、类型判断 => Object.prototype.toString.call

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
