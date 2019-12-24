# 插件机制

```
class BasicPlugin{ 
    constructor(pluginOptions) {
        this.options = pluginOptions;
    } 
    // 定义一个 apply 函数，并注入了 compiler 对象
    apply(compiler) { 
        // 挂载 webpack 事件钩子（这里挂载的是 emit 事件）
        compiler.plugin('emit', function (compilation, callback) {
            // 操作 compilation 对象的内部数据
            console.log(compilation);
            // 执行 callback 回调
            callback();
        });
    }
} 
module.exports = BasicPlugin;
```
