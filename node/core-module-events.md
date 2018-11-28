# Events Module
- 打印`events`对象
- Events Module简介
- 向监听器传参
- 异步VS同步
- 单次处理事件
- error事件
- class
    - events.EventEmitter()

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

## Events Module简介
- `events`是Node.js的内置模块。（无需额外安装）
- `events`是一个构造函数。
- `events`模块提供了一种使用事件的方式。使用`events`模块，我们可以：
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
## 向监听器传参
## 异步VS同步
## 单次处理事件
## error事件
## event.EventEmitter()
- `EventEmitter`是一个类，由`events`模块定义并暴露。
- EventEmitter用于创建事件对象。

```
const events = require('events)
const em = new events.eventEmitter()
```

## em.on(eventName,listener)
数据类型：Function
用途：为事件对象指定事件类型、添加事件处理程序。通常，事件名称是camel-cased字符串，但可以使用任何有效的JavaScript属性键。
- 参数：
  - eventName: string
  - listener: function

## em.emit(eventName,[...args])
- 数据类型：Function
- 用途：用于触发事件。
- 参数：
  - eventName: string  
  - args: any