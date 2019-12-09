# 前端常见设计模式

在面向对象软件设计过程中针对特定问题的简洁而优雅的解决方案

### 面向对象

把客观对象抽象成属性数据和对数据的相关操作，把内部细节和不想关的信息隐藏起来，把同一个类型的客观对象的属性数据和操作绑定在一起，封装成类，并且允许分成不同层次进行抽象，通过继承实现属性和操作的共享

* 面向对象的分析 OOA
* 面向对象的设计 OOD
* 面向对象的编程 OOP

#### 继承

* 子类继承父类
* 继承可以把公共方法抽离出来，提高复用，减少冗余

#### 封装

* 数据封装起来
* 减少耦合，不该外部访问的不要让外部访问
* 利于数据的接口权限管理
* ES6 目前不支持，一般认为_开头的都会私有的，不要使用
* public:公有修饰符，可以在类内或者类外使用public修饰的属性或者行为，默认修饰符
* protected:受保护的修饰符，可以本类和子类中使用protected修饰的属性和行为
* private:私有修饰符，只可以在类内使用private修饰的属性和行为

#### 多态

* 同一个接口可以不同实现
* 保持子类的开放性和灵活性
* 面向接口编程

```
class Animal {
    public name;
    protected age;
    private weight;
    constructor(name,age,weight) {
        this.name=name;
        this.age=age;
        this.weight=weight;
    }
}
class Person extends Animal {
    private money;
    constructor(name,age,weight,money) {
        super(name,age,weight);
        this.money=money;
    }
    speak() {
        console.log('你好!');
    }    
}
class Dog extends Animal {
    private money;
    constructor(name,age,weight) {
        super(name,age,weight);
    }
    speak() {
        console.log('汪汪汪!');
    }    
}

let p=new Person('zfpx',10,10,10);
p.speak();
let d=new Dog('zfpx',10,10);
d.speak();
```

### 设计原则

SOLID五大设计原则

首字母 |	指代	| 概念
:-: | :-: | :-: 
S |	单一职责原则	| 单一功能原则认为对象应该仅具有一种单一功能的概念。
O |	开放封闭原则	| 开闭原则认为“软件体应该是对于扩展开放的，但是对于修改封闭的”的概念。
L |	里氏替换原则	| 里氏替换原则认为“程序中的对象应该是可以在不改变程序正确性的前提下被它的子类所替换的”的概念。参考 契约式设计。
I |	接口隔离原则	| 接口隔离原则认为“多个特定客户端接口要好于一个宽泛用途的接口”[5] 的概念。
D |	依赖反转原则	| 依赖反转原则认为一个方法应该遵从“依赖于抽象而不是一个实例”[5] 的概念。依赖注入是该原则的一种实现方式。

### 工厂模式

### 单例模式

### 适配器模式

### 装饰器模式

### 观察者模式/发布订阅模式

### 代理模式
