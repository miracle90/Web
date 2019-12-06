# 事件机制

### 事件触发三阶段

* window 往事件触发处传播，遇到注册的捕获事件会触发
* 传播到事件触发处时触发注册的事件
* 从事件触发处往 window 传播，遇到注册的冒泡事件会触发

### 事件注册

* addEventListener
* 第三个参数，默认false，决定了注册的事件是捕获事件还是冒泡事件
* stopPropagation，用来阻止事件冒泡的，其实该函数也可以阻止捕获事件
* stopImmediatePropagation 同样也能实现阻止事件，但是还能阻止该事件目标执行别的注册事件
* e.target 和 e.currentTarget

### 事件代理

如果一个节点中的子节点是动态生成的，那么子节点需要注册事件的话应该注册在父节点上

``` javascript
<ul id="ul">
	<li>1</li>
	<li>2</li>
	<li>3</li>
	<li>4</li>
	<li>5</li>
</ul>
<script>
	let ul = document.querySelector('#ul')
	ul.addEventListener('click', (event) => {
		console.log(event.target);
	})
</script>
```

事件代理的方式相较于直接给目标注册事件来说，有以下优点：

* 节省内存
* 不需要给子节点注销事件

