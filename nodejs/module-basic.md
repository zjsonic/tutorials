## 什么是Module
- module是Node.js中的一个内置对象。
 `module` 是一个对象
```
{
  id: '.',
  exports: {},
  parent: null,
  filename: '/Users/zj/my-projects/learn-node/app.js',
  loaded: false,
  children: [],
  paths: [ '/node_modules' ]
}
```
`module.__proto__`对象定义了方法
```
{
  load: [Function],
  require: [Function],
  _compile: [Function]
}
```
- Node.js中的module是一个简单又复杂的功能。
    - 形式：module由一个或多个js文件构成。（每个module可以放在一个单独的js文件中）
    - 复用：module在整个项目中可以复用。
    - 作用域：每个module有自己的context,因此它不会和其他模块冲突或污染全局范围。

## 使用module.require()方法导入module文件
Node.js在引入module时，执行CommonJS Modules Standard。
`module.require()` = `require()` 后者为前者的快捷方式。
使用方法如下：
1. 直接引入module名称
引入`node_modules`文件夹中的`module`时，直接引入module名称即可
```
const http = require('http')  // module name : 'http' (string)
```
2. 使用相对路径引入module名称
在导入`local module`或`json`文件时，需要使用相对路径
```
const orderRoutes = require('./api/routes/orders')
```
3. 文件扩展名可省略
Node.js的检索文件扩展名顺序：
- js
- json
4. requrie()函数会返回一个对象、函数、属性或其他JS类型，取决于指定模块的返回值


## Node.js的module类型
- core modules（Node.js的核心模块被编译成了二进制文件，核心模块位于Node.js源代码的lib文件夹中。核心模块始终优先加载，即使存在该名称的文件）
    - http
    - url
    - queryString
    - path
    - fs
    - util
- local modules:指Node.js项目中由开发者创建的模块。
- third party modules



## 例：引入一个全局模块
使用Node.js的http模块创建一个服务器
```
const http = require('http')
const server = http.createServer(function(req,res){
  //code
})
server.listen(8000)
```
- require()函数返回了一个对象，因为http模块把它的功能作为一个对象返回。
- 通过点语法，可以使用http对象的属性和方法

## 例：引入一个本地模块
手写一个简单的logging模块，记录信息、警告或错误以便console
```
const log = {
  info: function (info) {
    console.log(infor)
  },
  warning: function (warning) {
    console.log(warning)
  },
  error: function (error) {
    console.log(error)
  }
}

module.exports = log 
```
注：记得使用module.exports 把log对象当做一个模块暴露出来

## module.exports
`module.exports`是module系统创建的对象。
- 输出文本
- 输出对象
- 输出对象的属性或方法(返回值是一个对象)
- 输出函数
- 输出函数做为类
```
module.exports.name = person['first name']   // return { 'first name': 'zhang san'}
module.exports.act = person.act   // return { act: [ Function: act ] }
```