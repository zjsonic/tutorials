# Events Module
- 打印`events`对象
- 向监听器传参
- 异步VS同步
- 单次处理事件
- error事件
- class
    - events.EventEmitter

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
很多Node.js核心API都是围绕一个惯用的异步事件驱动架构构建的，其中某些类型的对象（称为“发射器”）发出命名事件，导致调用Function对象（“侦听器”）。例如:

- 每次客户端连接服务器的时候，`net.Server`对象会发出事件；
- 每次文件被打开的时候，`fs.readStream`对象会发出事件
- 只要有数据可供读取，`stream`就会发出事件。

发出事件的所有对象都是EventEmitter类的实例。 这些对象暴露了`eventEmitter.on（）`函数，该函数允许将一个或多个函数附加到对象发出的命名事件。 通常，事件名称是camel-cased字符串，但可以使用任何有效的JavaScript属性键。

当EventEmitter对象发出事件时，将同步调用附加到该特定事件的所有函数。 被调用侦听器返回的任何值都将被忽略，并将被丢弃。

以下示例显示了具有单个侦听器的简单EventEmitter实例。 eventEmitter.on（）方法用于注册侦听器，而eventEmitter.emit（）方法用于触发事件。

```
const EventEmitter = require('events');

class MyEmitter extends EventEmitter {}

const myEmitter = new MyEmitter();
myEmitter.on('event', () => {
  console.log('an event occurred!');
});
myEmitter.emit('event');
```
## 向监听器传参
## 异步VS同步
## 单次处理事件
## error事件
## eventEmitter
- eventEmitter是由`events`模块定义和暴露的。
Node中的许多对象都会发出事件。
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