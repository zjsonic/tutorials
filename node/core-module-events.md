# Events Module
- Events Module简介
- 向监听器传参
- 异步VS同步
- 单次处理事件
- error事件
- events.EventEmitter()类
- 打印`events`对象


## Events Module简介
- `events`是一个构造函数。
- `events`模块提供了一种使用事件的方式。
- 使用`events`模块，我们可以：
  - 创建事件对象
  - 设置事件类型
  - 添加事件监听程序
  - 触发事件

```
const events = require('events');

class myEvents extends events {}

const myEmitter = new MyEmitter();
myEmitter.on('event', () => {
  console.log('an event occurred!');
});
myEmitter.emit('event');
```
或
```
const events = require('events') // 引入events模块

const em = new events.EventEmitter() //创建EventEmitter类的实例

em.on('myEvent',(data) => {  //在事件对象上指定事件类型和事件处理函数
    console.log('My event occurred' + data)
})

em.emit('myEvent','This is my first Node.js event emitter example.') //触发指定事件，并把参数传递给事件处理程序
```

## event.EventEmitter()
- `EventEmitter`是一个类，由`events`模块定义并暴露。
- `EventEmitter`是一个能触发事件的对象。
- 所有能触发事件的对象都是`EventEmitter`类的实例。这些对象有一个eventEmitter.on() 函数，用于将一个或多个函数绑定到命名事件上。 事件的命名通常是驼峰式的字符串
  - net.Server 会在每次有新连接时触发事件
  - fs.ReadStream 会在文件被打开时触发事件
  - stream会在数据可读时触发事件。
- 当 `EventEmitter` 对象触发一个事件时，所有绑定在该事件上的函数都会被同步地调用。

```
const events = require('events)
const em = new events.eventEmitter()
```

## em.on(eventName,listener)
- 数据类型：Function
- 用途：为事件对象指定事件类型、添加事件处理程序。
- 参数：
  - eventName: string
  - listener: function
- 返回值：EventEmitter（可以形成chains)

## em.emit(eventName,[...args])
- 数据类型：Function
- 用途：用于触发事件。
- 参数：
  - eventName: string (通常是camel-cased字符串，也可以是任何有效的JavaScript key) 
  - args: any
- 返回值：boolean



## 打印events对象
```
{
  [Function: EventEmitter]
  EventEmitter: [Circular],
  usingDomains: true,
  defaultMaxListeners: [Getter/Setter],
  init: [Function],
  listenerCount: [Function] 
}
```
打印`events.prototype`

```
EventEmitter {
  domain: undefined,
  _events: undefined,
  _maxListeners: undefined,
  setMaxListeners: [Function: setMaxListeners],
  getMaxListeners: [Function: getMaxListeners],
  emit: [Function: emit], //emit(eventName,[args]) 同步调用每一个使用eventName名称注册的监听器，并将提供的参数传递给每个监听器   
  addListener: [Function: addListener],
  on: [Function: addListener],
  prependListener: [Function: prependListener],
  once: [Function: once],
  prependOnceListener: [Function: prependOnceListener],
  removeListener: [Function: removeListener],
  removeAllListeners: [Function: removeAllListeners],
  listeners: [Function: listeners],
  listenerCount: [Function: listenerCount],
  eventNames: [Function: eventNames] }
```