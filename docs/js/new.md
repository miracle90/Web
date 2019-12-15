# new

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

对于创建一个对象来说，更推荐使用字面量的方式创建对象（无论性能上还是可读性）。

因为你使用 new Object() 的方式创建对象需要通过作用域链一层层找到 Object，但是你使用字面量的方式就没这个问题。
