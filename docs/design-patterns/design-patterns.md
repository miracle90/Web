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

可以想象一个场景。假设有一份很复杂的代码需要用户去调用，但是用户并不关心这些复杂的代码，只需要你提供给我一个接口去调用，用户只负责传递需要的参数，至于这些参数怎么使用，内部有什么逻辑是不关心的，只需要你最后返回我一个实例。这个构造过程就是工厂。

工厂起到的作用就是隐藏了创建实例的复杂度，只需要提供一个接口，简单清晰。

* 简单工厂模式：简单工厂模式是由一个工厂对象决定创建出哪一种产品类的实例
* 工厂方法模式：在工厂方法模式中，核心的工厂类不再负责所有的产品的创建，而是将具体创建的工作交给子类去做
* 抽象工厂模式：抽象工厂模式可以向客户端提供一个接口，使客户端在不必指定产品的具体的情况下，创建多个产品族中的产品对象

```
// 抽象工厂模式
class Button{
    render() {

    }
}
class AppleButton{
    render() {
       console.log('苹果按钮');
    }
}
class WindowButton{
    render() {
       console.log('Windows按钮');
    }
}

class Icon{
    render() {

    }
}
class AppleIcon{
    render() {
       console.log('苹果图标');
    }
}
class WindowIcon{
    render() {
       console.log('Windows图标');
    }
}
class Factory{
    createButton() {}
    createIcon() {}
}
class AppleFactory{
    createButton() {
        return new AppleButton();
    }
    createIcon() {
        return new AppleButton();
    }
}
class WindowsFactory{
    createButton() {
        return new WindowButton();
    }
    createIcon() {
        return new WindowIcon();
    }
}
const settings={
    'apple': AppleFactory,
    'windows':WindowsFactory
}
let appleFactory=new settings['apple']();
appleFactory.createButton().render();
appleFactory.createIcon().render();

let windowsFactory=new settings['windows']();
windowsFactory.createButton().render();
windowsFactory.createIcon().render();
```

### 单例模式

单例模式很常用，比如全局缓存、全局状态管理等等这些只需要一个对象，就可以使用单例模式。

单例模式的核心就是保证全局只有一个对象可以访问。因为 JS 是门无类的语言，所以别的语言实现单例的方式并不能套入 JS 中，我们只需要用一个变量确保实例只创建一次就行，以下是如何实现单例模式的例子

```
class Singleton {
  constructor() {}
}

Singleton.getInstance = (function() {
  let instance
  return function() {
    if (!instance) {
      instance = new Singleton()
    }
    return instance
  }
})()

let s1 = Singleton.getInstance()
let s2 = Singleton.getInstance()
console.log(s1 === s2) // true
```

### 适配器模式

适配器用来解决两个接口不兼容的情况，不需要改变已有的接口，通过包装一层的方式实现两个接口的正常协作。

* 插件适配
* promisify
* computed

```
class Power{
    charge() {
        return '220V';
    }
}

class Adapter{
    constructor() {
        this.power=new Power();
    }
    charge() {
        let power=this.power.charge();
        return `${power} => 12V`;
    }
}

class Client{
    constructor() {
        this.adapter=new Adapter();
    }
    use() {
        console.log(this.adapter.charge());
    }
}
new Client().use();
```

### 装饰器模式

* 在不改变其原有的结构和功能为对象添加新功能
* 装饰比继承更加灵活

装饰器模式是将一个对象嵌入另一个对象之中，实际上相当于这个对象被另一个对象包装起来，形成一条包装链。请求随着这条链条依次传递到所有的对象，每个对象有处理这个请求的机会。

```
class Coffee{
  make(water){
    return `${water}+咖啡`;
  }
  cost(){
      return 10;
  }
}

class MilkCoffee{
    constructor(parent){
        this.parent = parent;
    }
    make(water){
        return `${this.parent.make(water)}+牛奶`;
    }
    cost(){
        return this.parent.cost()+1;
    }
}

class SugerCoffee{
    constructor(parent){
        this.parent = parent;
    }
    make(water){
        return `${this.parent.make(water)}+糖`;
    }
    cost(){
        return this.parent.cost()+2;
    }
}
let coffee = new Coffee();
let milkCoffee = new MilkCoffee(coffee);
let milksugerCoffee = new SugerCoffee(milkCoffee);
console.log(milksugerCoffee.make('水')+'='+milksugerCoffee.cost());
```

* 埋点
* 表单校验
* 防CSRF攻击
* 支持decorators

### 观察者模式/发布订阅模式

观察者模式两个对象之间有很强的依赖关系；发布/订阅模式两个对象之间的耦合度低

```
class Star{
    constructor(name) {
        this.name=name;
        this.state='';
        this.observers=[];
    }
    getState() {
        return this.state;
    }
    setState(state) {
        this.state=state;
        this.notifyAllObservers();
    }
    attach(observer) {
        this.observers.push(observer);
    }
    notifyAllObservers() {
        this.observers.forEach(observer=>observer.update());
    }
}
class Fan{
    constructor(name,subject) {
        this.name=name;
        this.subject=subject;
        this.subject.attach(this);
    }
    update() {
        console.log(`${this.subject.name}有新的状态-${this.subject.getState()},${this.name}正在更新`);    
    }
}
let star=new Star('赵丽颖');
let fan1=new Fan('姜老师',star);
star.setState('结婚');
```

* 事件绑定
* Promise
* events

### 代理模式

由于一个对象不能直接引用另外一个对象，所以需要通过代理对象在这两个对象之间起到中介作用，可以在使用者和目标对象之间加一个代理对象,通过代理可以实现控制

* 事件委托
* 图片懒加载
* 防抖代理
* 代理跨域

```
class Goole{
    constructor() {    }
    get() {
        return 'google';
    }
}

class Proxy {
    constructor() {
        this.google=new Goole();
    }
    get() {
        return this.google.get();
    }
}
let proxy = new Proxy();
let ret = proxy.get();
console.log(ret);
```
