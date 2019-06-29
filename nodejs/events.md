[TOC]

# Events Module

- Events module is a built-in module in Node.js. 

- The events module provides a way of working with events. Events module is used to:
  + Create your own events
  + Fire(emit) your own events
  + Listen for your own events

## events and EventEmitter

Print `events` module:  function EventEmitter(){}

```javascript
{
  [Function: EventEmitter]
  EventEmitter: [Circular],
  usingDomains: true,
  defaultMaxListeners: [Getter/Setter],
  init: [Function],
  listenerCount: [Function] 
}
```

Print `EventEmitter` class directly

```javascript
ReferenceError: EventEmitter is not defined
```

Print `events.EventEmitter` class

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

Events module and EventEmitter class

```javascript
events === events.EventEmitter // true
```

`events.EventEmitter` class is the only class exported by `events` module.

- `EventEmitter`是一个类，由`events`模块定义并暴露。
- `EventEmitter`是一个能触发事件的对象。
- 所有能触发事件的对象都是`EventEmitter`类的实例。

include the events module

```javascript
const events = require('events')
```

or

```javascript
const EventEmitter = require('events')
```

## Create an EventEmitter Object

```
const events = require('events')
const myEmitter = new events.EventEmitter
console.log(myEmitter)

//returns the EventEmitter object
EventEmitter {
  _events: [Object: null prototype] {},
  _eventsCount: 0,
  _maxListeners: undefined }
```
Or 
```
onst EventEmitter = require('events')
const myEmitter = new EventEmitter
console.log(myEmitter)

//returns the EventEmitter object
EventEmitter {
  _events: [Object: null prototype] {},
  _eventsCount: 0,
  _maxListeners: undefined }
```

Or 

```javascript
const events = require('events')
class myEvents extends events {}
const myEmitter = new myEvents
console.log(myEmitter)

//returns the EventEmitter object
EventEmitter {
  _events: [Object: null prototype] {},
  _eventsCount: 0,
  _maxListeners: undefined }
```

## emitter.on(eventName,listener)
Adds the listener function for the event named 'eventname'.

- eventName: string | symbol
- Listener: function 
- Return: `EventEmitter`  (so that calls can be chained.)

## emitter.emit(eventName,[...args])
Synchronously calls each of the listeners and passes the supplied arguments to each.

- eventName: `<string>` | `<symbol>` 
- ..args: `<any>` 
- Returns: `<boolean>`  (True if the event had listener,false otherwise.)

## events.prototype

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