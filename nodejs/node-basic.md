## 安装Node.js
- 可以从官网(https://nodejs.org/en/download/)直接下载
- 可以通过各种package manager安装

## 什么是Node.js
Node.js是基于Chrome的V8引擎构建的JS运行环境。常用来创建web服务器。Node.js可以做一下事情：
- 操作内容：生成动态内容
- 操作文件：可以操作服务器上的文件
- 操作表单：可以操作表单数据
- 操作数据库：可以操作数据库的数据

## 什么是NPM
- NPM即Node.js Package Manager。
- NPM是为JS语言设计的包管理工具。
- NPM是Node.js平台默认的包管理工具。
- Node.js捆绑了NPM,所以安装了Node.js即安装了NPM。
- 使用npm可以安装、管理项目中所使用的依赖。还可以分享代码，和他人交流。

## 查看版本
可以通过查看版本号测试安装是否成功。
```
$ node --version
```

```
$ npm --version
```

## 启动Node.js
启动Node.js就是启动Node.js的解释器。有两种方式：
方式一：启动Node交互模式
```
$ node
```

方式二：启动Node运行模式
```
$ node hello.js

```

## Node.js的数据类型
- 原始类型：
 - String
 - Number
 - Boolean
 - Undefined
 - Null
 - RegExp
- Object:
 - Object Literal
 - Function
 - Buffer:用于存储二进制数据
 - process Object
注：Node.js像Js一样，也支持松散类型：即使用var声明的任意类型的变量。

## 全局变量
- 浏览器：Window
- Node.js: Global

## 默认作用域
- 在浏览器端，不使用var声明一个变量, 默认为全局变量
- 在Node.js，不使用var声明一个变量，默认为local

## 创建全局方法或属性
- `module.exports`
- `exports`
```
exports.log = {
    console: function(msg) {
        console.log(msg);
    },
    file: function(msg) {
        // log to file here
      }
}
```
## 使用全局方法或属性
- `require()`

