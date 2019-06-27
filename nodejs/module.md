[TOC]

# Modules

## What is a module in Node.js

**In the Node.js modules system, each file is treated as a module.** 

- 形式：module由一个或多个js文件构成。（每个module可以放在一个单独的js文件中）
- 复用：module在整个项目中可以复用。
- 作用域：每个module有自己的context,因此它不会和其他模块冲突或污染全局范围。

## module object

In each module, the module variable is a reference to the object representing the current module.

- `module.id`
  + DataType: `<string>`
  + Description: The identifier for the module. Typically this is the resolved filename.
- `module.exports` 
  + DataType: `<object>`
  + Description: 
    * The `module.exports` is an object created by the Module system.
    * Any put into the the `module.exports` will get exported.
- `module.children` 
- `module.parent` 
- `module.filename` 
  + DataType: `<string>`
  + Description: The fully resolved file name of the module.
- `module.loaded` 
- `module.paths` 

## module.constructor

- `module.constructor.builtinModules` 

## module.constructor.prototype

- `module.constructor.prototype.require(id)` 
  - Description: provides a way to load a module(Node.js在引入module时，执行CommonJS Modules Standard。)
  - Id: string
  - Return: <anytype> Exported module content ( requrie()函数会返回一个对象、函数、属性或其他JS类型，取决于指定模块的返回值)
  - Usages
    * `module.require()` = `require()` 后者为前者的快捷方式。
    * 直接引入module名称: 引入`node_modules`文件夹中的`module`时，直接引入module名称即可
    * 使用相对路径引入module名称: 在导入`local module`或`json`文件时，需要使用相对路径
    * 文件扩展名可省略(Node.js的检索文件扩展名顺序: .js .json )
- `module.constructor.prototype.load()` 
- `module.constructor.prototype._compile()` 

## exports variable

- `exports` is a variable that is available within a module's file-level scope.
- `exports` is bound to `module.exports` : The `exports` variable is a reference to the `module.exports` object.

## Node.js Module Types

Node.js includes 3 types of modules:

- Core Modules：a set of built-in modules。
  + 核心模块位于Node.js源代码的lib文件夹中。
  + Node.js的核心模块被编译成了二进制文件。
  + You can use the core modules without any further installation.
  + 核心模块始终优先加载，即使存在该名称的文件。
- Local Modules： Node.js项目中由开发者创建的模块
- Third Party Modules

## Unfinished Copy

In order to prevent a infinite loop, an **unfinished copy**  of the a.js exports object is returned to the b.js module. b.js then finishes loading.

## File Modules

- If the exact filename is not found, then the Node.js will attempt to load the required filename with the added extensions: `.js`  > `.json` >  `.node` 

- A required module prefixed with `/` is a absolute path to the file.

- A required module prefixed with `./` is a relative path to the file.

- Without a leading `/` `./` `../` to indicate a file, the module must be a core module or loaded from the `node_modules` folder.

- If the given path does not exist, require() function will throw an error with its code property set to `MODULE_NOT_FOUND`. 

## Folders as Modules

If a folder is passed to require() as an argument: 

```javascript
require('./some_library')
```

First,  the `requrie('./some_library')`  will attempt to load the path of the main entry: `./some_library/libs/some_library.js` 

```javascript
// package.json
{
  "name": "some_library",
  "main": "./libs/some_library.js"
}
```

If there is no `package.json` file in the directory, or if the `main` entry is missing or cannot be resolved, then the Node.js will attempt to load `index.js` or `index.node` file out of that directory.

- `./some_library/index.js` 
- `./some_library/index.node` 

If these attempts fail, the Node.js will report the entire modules as missing with the default error:

```javascript
Error: Cannot find module 'some_library'
```

## Loading from node_modules folder

If the module identifier passed to `require()` is not a core module, and does not begin with `/`  `./` or `../` , then the node.js starts at the parent directory of the current module, and adds `/node_modules` , and attempt to load module from that location. 

If it is not found there, then it moves to the parent directory, and so on, until the root of the file system is reached.

- `/home/ry/projects/node_modules/bar.js`
- `/home/ry/node_modules/bar.js`
- `/home/node_modules/bar.js`
- `/node_modules/bar.js`

## Loading from the global folders

Sorry, no content.

## The Module Wrapper

Before a module's code is executed, Node.js will wrap it with a function wrapper that looks like the following: 

```JavaScript
(function( exports,require,module,__filename,__dirname ){
  //module code actually live in here.
})
```

## The Module Scope

### __dirname

- DataType:`string`
- Description: Get the directory name of the current module.

It is the same as the `path.dirname()` of the `__filename`.

```javascript
console.log(__dirname)
///prints: Users/zj/my-projects/learn/learn-nodejs/demo1
console.log(path.dirname(__filename))
///prints: Users/zj/my-projects/learn/learn-nodejs/demo1
```

### __filename

Get the filename of the current module.

## 例：引入一个全局模块

使用Node.js的http模块创建一个服务器

```js
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

```js
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

