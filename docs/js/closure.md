# 闭包

### 关键词

* 执行上下文
* VO 变量对象
* 作用域 + 作用域链

## 闭包的定义

闭包的定义其实很简单：函数 A 内部有一个函数 B，函数 B 可以访问到函数 A 中的变量，那么函数 B 就是闭包。

```
function A() {
  let a = 1
  window.B = function () {
      console.log(a)
  }
}
A()
B() // 1
```

在 JS 中，闭包存在的意义就是让我们可以间接访问函数内部的变量。

```
// 闭包解决var问题
for (var i = 1; i <= 5; i++) {
  ;(function(j) {
    setTimeout(function timer() {
      console.log(j)
    }, j * 1000)
  })(i)
}
```

## 闭包的原理

执行上下文

### 执行上下文是什么？

可以简单理解执行上下文是js代码执行的环境，当js执行一段可执行代码时，会创建对应的执行上下文

```
executionContextObj = {
	this: 对的就是你关注的那个this,
	VO：变量对象,
  scopeChain: 作用域链,跟闭包相关
}
```

### 创建闭包的过程

1. 运行函数a

创建函数a的VO，包括变量num和函数b

定义函数b的时候，会保存a的变量对象VO和全局变量对象到[[scope]]中

返回函数b，保存到c1

2. 运行c1

创建c1的作用域链，该作用域链保存了a的变量对象VO

创建c1的VO

运行c1，这是发现需要访问变量num，在当前VO中不存在，于是通过作用域链进行访问，找到了保存在a的VO中的num，对它进行操作，num的值被设置成2

3. 再次运行c1，重复第二步的操作，num的值设置成3

```
function a() {
	var num = 1
	function b() {
		console.log(num++)
	}
	return b
}
var c1 = a()
c1() // '1'
c1() // '2'
var c2 = a()
c2() // '1'
c2() // '2'
```
