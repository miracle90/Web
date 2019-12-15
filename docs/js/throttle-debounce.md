# 节流防抖

结合应用场景

### 防抖 debounce

* search搜索联想，用户在不断输入值时，用防抖来节约请求资源。
* window触发resize的时候，不断的调整浏览器窗口大小会不断的触发这个事件，用防抖来让其只触发一次

### 源码

核心思想：每次触发清除定时器，新建一个

```
function debounce(method, delay) {
  var timer = null;
  return function () {
    var context = this, args = arguments;
    clearTimeout(timer);
    timer = setTimeout(function () {
      method.apply(context, args);
    }, delay);
  }
}
```

### 节流 throttle

* 鼠标不断点击触发，mousedown(单位时间内只触发一次)
* 监听滚动事件，比如是否滑到底部自动加载更多，用throttle来判断
* 窗口调整（resize）
(抢购疯狂点击（mousedown）

### 源码

核心思想：触发时间和上一次时间比对

```
function throttle(method, delay) {
  var last = 0;
  return function () {
    var now = +new Date();
    if (now - last > delay) {
      method.apply(this, arguments);
      last = now;
    }
  }
}
```
