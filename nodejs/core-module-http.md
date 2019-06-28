[TOC]

# HTTP

- HTTP interfaces in Node.js are designed to support many features of the HTTP protocol which have been traditionally difficult to use.

- `http`是服务器与客户端通信的一个接口。
- `http`是一个接口对象。
- `http`是Node.js的一个核心模块。
- HTTP API是非常底层的，只涉及处理流和简单解析消息。
网络数据的传输是通过一系列实现的，而Node.js帮助我们处理了这些协议，并提供了`http`接口。

## http暴露的接口
- class
  - http.Server: 用来实例化一个http server
  - http.ClientRequest: 用来实例化一个http请求
  - http.ServerResponse: 用来实例化一个http响应
  - http.IncomingMessage: 用来实例化一个请求信息对象
  - http.Agent
- properties
  - http.METHODS
  - http.STATUSCODES
  - http.globalAgent
- methods
    - http.createServer([options],[requestListener]): http.Server的语法糖
    - http.get(options,[callback]): http.ClientRequest的语法糖
    - http.get(url,[options],[callback]): http.ClientRequest的语法糖
    - http.request(options,[callback]): http.ServerResponse的语法糖
    - http.request(url,[options],[callback]): http.ServerResponse的语法糖

## http.Server和http.createServer

[https://github.com/nodejs/node-v0.x-archive/blob/master/lib/http.js#L1674](https://github.com/nodejs/node-v0.x-archive/blob/master/lib/http.js#L1674)
```
exports.Server = Server;
exports.createServer = function(requestListener) {
  return new Server(requestListener);
};
```
```
http.createServer = function (requestListener) {
     var ser = new http.Server();
     ser.addListener(requestListener);
     return ser;
};
```


## http.Server
- `http.Server`继承自`net.Server` 用于创建http服务器
  - `net.Server`是另一个类，用于创建TCP或IPC服务器。
  - `net.Server`是一个`EventEmitter`。
- `http.Server`是一个基于事件的HTTP服务器
  - 所有的请求都被封装到独立的事件当中
  - 我们只需要对他的事件编写相应的行数就可以实现HTTP服务器的所有功能


- server.request： 自有事件,只要有请求，就会触发request事件，每个connection可能会存在多个请求。
- server.close() : 关闭服务器连接
- server.listen() : 监听计算机端口
- server.listening : 检测服务器是否正在监听连接

## METHODS: http.createServer([options],[requestListener])
- 用途: 用于创建HTTP服务器。
- 返回值: `http.Server`
- 参数:
  - options:`<object>`
    - IncomingMessage: 拓展默认的http.IncomingMessage类。
    - ServerResponse: 拓展默认的http.ServerResponse类。
  - requestListener:`<function>`
    - 用途：`http.Server.request`事件上的处理函数。一旦有请求进来，即会调用该函数。





## CLASS: http.ClientRequest()
- 类型：http.ClientRequest是一个类，也就是一个构造函数。
```
{ [Function: ClientRequest]
  super_:
   { [Function: OutgoingMessage]
     super_:
      { [Function: Stream]
        super_: [Object],
        Readable: [Object],
        Writable: [Object],
        Duplex: [Object],
        Transform: [Object],
        PassThrough: [Object],
        Stream: [Circular],
        _isUint8Array: [Function: isUint8Array],
        _uint8ArrayToBuffer: [Function: _uint8ArrayToBuffer] } } }
```
- `http.ClientRequest`是`http.request()`方法的返回值。
- `http.ClientRequest`表示请求队列中正在进行的请求。
- 使用以下API可以修改`header`:
  - request.setHeader(name,value)
  - request.getHeader(name)
  - request.removeHeader(name)
- 实际的heaer将与第一个数据块一起发送，或者在调用request.end()时发送。
- 要获得响应，请为request对象添加“response”侦听器。 收到响应头后，将从request对象发出'response'。
- 'response'事件使用一个参数执行，该参数是http.IncomingMessage的一个实例。
- 在“响应”事件期间，可以向响应对象添加侦听器；特别是侦听“数据”事件。
- 如果未添加“响应”处理程序，则将完全丢弃响应。
- 但是，如果添加了“响应”事件处理程序，则必须使用来自响应对象的数据，无论是在存在“可读”事件时调用response.read()，还是通过添加“数据”处理程序，或通过调用.install()方法。在使用数据之前，“结束”事件不会激发。此外，在读取数据之前，它将消耗内存，这最终会导致“内存不足进程”错误。

## CLASS: http.IncomingMessage
- 类型：类 构造函数
- 由`http.ClientRequest`或`http.Server`创建
- 它作为第一个参数，被分别地传入到`request`和`response`事件中
- 它可以用于获取response.status、header和data


## CLASS: http.ServerResponse
- 此对象是由HTTP服务器在内部创建的，而不是由用户创建的。它作为第二个参数传递给`request`事件。
- 响应继承了Stream，还实现了以下功能：






