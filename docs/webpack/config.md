# webpack

## 基础配置

* entry
* output
* devServer
* mode
* module
* plugins
* externals
* optimization => minimizer
* devtools: 'souce-map'
* watch: true 监听打包
* 代理

## 常用plugin

* html-webpack-plugin 生成html
* mini-css-extract-plugin 抽离css样式，变成link标签引入
* optimize-css-assets-webpack-plugin 优化css插件
* uglifyjs-webpack-plugin 通过UglifyES压缩ES6代码
* Webpack.ProvidePlugin 给每个模块注入一个插件
* Webpack.DefinePlugin 定义环境变量
* Webpack.BannerPlugin
* CopyWebpackPlugin
* commons-chunk-plugin 提取公共代码
* webpack-merge

## 常用loader

* css-loader 将css转成css模块，在webpack中引入
* style-loader 将css模块，以style标签形式插入到head标签中
* less-loader、stylus-loader、node-sass + sass-loader 处理css预处理器
* postcss-loader autoprefixer 给css属性加前缀
* file-loader：把文件输出到一个文件夹中，在代码中通过相对 URL 去引用输出的文件
* html-withimg-loader html中携带图片

* url-loader：和 file-loader 类似，但是能在文件很小的情况下以 base64 的方式把文件内容注入到代码中去
* source-map-loader：加载额外的 Source Map 文件，以方便断点调试
* image-loader：加载并且压缩图片文件
* babel-loader：把 ES6 转换成 ES5
* css-loader：加载 CSS，支持模块化、压缩、文件导入等特性
* style-loader：把 CSS 代码注入到 JavaScript 中，通过 DOM 操作去加载 CSS
* eslint-loader：通过 ESLint 检查 JavaScript 代码

## 性能优化

* noParse
* new Webpack.IgnorePlugin
* happypack 开启多进程打包
* tree-shaking 默认只支持es6语法，require不会去分析依赖
* scope hosting 作用域分析，webpack直接输出结果
* 抽取公共模块，只做多页面上使用

## 常见面试题

1. webpack与grunt、gulp的不同？
2. 与webpack类似的工具还有哪些？谈谈你为什么最终选择（或放弃）使用webpack？
3. 有哪些常见的Loader？他们是解决什么问题的？
4. 有哪些常见的Plugin？他们是解决什么问题的？
5. Loader和Plugin的不同？
6. webpack的构建流程是什么?从读取配置到输出文件这个过程尽量说全
7. 是否写过Loader和Plugin？描述一下编写loader或plugin的思路？
8. webpack的热更新是如何做到的？说明其原理？
9. 如何利用webpack来优化前端性能？（提高性能和体验）
10. 如何提高webpack的构建速度？
11. 怎么配置单页应用？怎么配置多页应用？
12. npm打包时需要注意哪些？如何利用webpack来更好的构建？
13. 如何在vue项目中实现按需加载？
* 使用 webpack 打包时，如何更好地利用 long term cache
* 随着 http2 的发展，webpack 有没有更好的打包方案
* webpack 中 tree shaking 的原理是什么
* vue-loader 的实现原理是什么

