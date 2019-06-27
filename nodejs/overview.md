## # Overview

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

- global
- Buffer()
- setInterval()
- clearInterval()
- setTimeout()
- clearTimeout()
- setImmediate()
- clearImmediate()
- process
- URL
- URLSearchParams
- WebAssembly

## 准全局变量

- `__dirname`: The directory of the current module. They exist only in the scope of modules.
- `__filename`
- `module.exports`
- `module`
- `module.constructor.prototype.require()`

## modules

In the Node.js modules system, each file is treated as a seperate module.

## 默认作用域

- 在浏览器端，若不使用var声明一个变量, 默认为全局变量
- 在Node.js，若不使用var声明一个变量，默认为local

## 创建全局方法或属性

- `module.exports`
- `exports`

```javascript
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