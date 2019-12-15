# 深浅拷贝

其实深拷贝和浅拷贝的主要区别就是其在内存中的存储类型不同。

堆和栈都是内存中划分出来用来存储的区域。

`栈（stack）为自动分配的内存空间，它由系统自动释放；而堆（heap）则是动态分配的内存，大小不定也不会自动释放。`

#### 基本数据类型存放在栈中
存放在栈内存中的简单数据段，数据大小确定，内存空间大小可以分配，是直接按值存放的，所以可以直接访问。

#### 引用类型（object）是存放在堆内存中的，变量实际上是一个存放在栈内存的指针，这个指针指向堆内存中的地址。每个空间大小不一样，要根据情况开进行特定的分配

### 浅拷贝

* Object.assign
* Array.prototype.concat()
* Array.prototype.slice()
* 展开运算符 ...

浅拷贝只解决了第一层的问题，如果接下去的值中还有对象的话，那么就又回到最开始的话题了，两者享有相同的地址。要解决这个问题，我们就得使用深拷贝了。

### 深拷贝

* JSON.parse(JSON.stringify(object))
* 手写递归方法

手写

```
let student = {
    name: 'lyy',
    age: 28,
    a: null,
    b: /reg/,
    d: new Date(),
    fn: function () {},
    obj1: {
        obj2: 1
    }
}

function deepClone(obj) {
    // 如果是 undefined 或者 null，null == undefined true
    if (obj == null) return obj     
    // 如果是时间类型
    if (obj instanceof Date) return new Date(obj)
    // 如果是正则
    if (obj instanceof RegExp) return new RegExp(obj)
    // 如果不是对象，不用拷贝，直接 return
    if (typeof obj !== 'object') return obj
    // 如果是对象或者数组,生成一个新的
    let newObj = new obj.constructor
    for (let key in obj) {
        if (obj.hasOwnProperty(key)) {
            newObj[key] = deepClone(obj[key])
        }
    }
    return newObj
}
console.log(deepClone(student))
```


Zepto 的 extend 方法
```
// 内部方法：用户合并一个或多个对象到第一个对象
// 参数：
// target 目标对象  对象都合并到target里
// source 合并对象
// deep 是否执行深度合并
function extend(target, source, deep) {
    for (key in source)
        if (deep && (isPlainObject(source[key]) || isArray(source[key]))) {
            // source[key] 是对象，而 target[key] 不是对象， 则 target[key] = {} 初始化一下，否则递归会出错的
            if (isPlainObject(source[key]) && !isPlainObject(target[key]))
                target[key] = {}

            // source[key] 是数组，而 target[key] 不是数组，则 target[key] = [] 初始化一下，否则递归会出错的
            if (isArray(source[key]) && !isArray(target[key]))
                target[key] = []
            // 执行递归
            extend(target[key], source[key], deep)
        }
        // 不满足以上条件，说明 source[key] 是一般的值类型，直接赋值给 target 就是了
        else if (source[key] !== undefined) target[key] = source[key]
}

// Copy all but undefined properties from one or more
// objects to the `target` object.
$.extend = function(target){
    var deep, args = slice.call(arguments, 1);

    //第一个参数为boolean值时，表示是否深度合并
    if (typeof target == 'boolean') {
        deep = target;
        //target取第二个参数
        target = args.shift()
    }
    // 遍历后面的参数，都合并到target上
    args.forEach(function(arg){ extend(target, arg, deep) })
    return target
}
```
