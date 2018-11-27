# Events Module
- 向监听器传参
- 异步VS同步
- 单次处理事件
- error事件
- class
    - events.EventEmitter


## 向监听器传参
## 异步VS同步
## 单次处理事件
## error事件
## eventEmitter
- eventEmitter是由`events`模块定义和暴露的。
Node中的许多对象都会发出事件。例如，
- 每次客户端连接服务器的时候，net.Server对象会发出事件；
- 每次文件被打开的时候，fs.readStream对象会发出事件
所有能触发事件的对象都是events.EventEmitter类的实例。
eventEmitter类属于events模块。可以通过下列代码访问eventEmitter
```
const events = require('events)
const eventEmitter = new events.eventEmitter()
```
当`eventEmitter`实例遇到任何错误，它会发出一个`error`事件。
当一个新的listener被建立，新的监听事件会被触发。
当一个listener被删除的时候，删除监听的事件会被触发。

eventEmitter提供了多个属性：
- on:用于绑定事件处理函数
- emit：用于触发事件