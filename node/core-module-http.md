# Core Module: HTTP
- 打印HTTP
- HTTP简介
- class
    - http.Agent
    - http.Server
      - server.listen()
    - http.ClientRequest
    - http.IncomingMessage
    - http.ServerResponse
    
- properties
    - http.Methods
    - http.STATUSCODES
- methods
    - http.createServer([options],[requestListener])
    - http.get(options,[callback])
    - http.get(url,[options],[callback])
    - http.globalAgent
    - http.request(options,[callback])
    - http.request(url,[options],[callback])


## 打印HTTP
`HTTP`
```
{ _connectionListener: [Function: connectionListener],
  METHODS:
   [ 'GET','POST','PUT','DELETE','HEAD','OPTIONS','PATCH'....],
  STATUS_CODES:
   { '100': 'Continue',
     '101': 'Switching Protocols',
     '102': 'Processing',
     '200': 'OK',
     '201': 'Created',
     '202': 'Accepted',
     '203': 'Non-Authoritative Information',
     '204': 'No Content',
     '205': 'Reset Content',
     '206': 'Partial Content',
     '207': 'Multi-Status',
     '208': 'Already Reported',
     '226': 'IM Used',
     '300': 'Multiple Choices',
     '301': 'Moved Permanently',
     '302': 'Found',
     '303': 'See Other',
     '304': 'Not Modified',
     '305': 'Use Proxy',
     '307': 'Temporary Redirect',
     '308': 'Permanent Redirect',
     '400': 'Bad Request',
     '401': 'Unauthorized',
     '402': 'Payment Required',
     '403': 'Forbidden',
     '404': 'Not Found',
     '405': 'Method Not Allowed',
     '406': 'Not Acceptable',
     '407': 'Proxy Authentication Required',
     '408': 'Request Timeout',
     '409': 'Conflict',
     '410': 'Gone',
     '411': 'Length Required',
     '412': 'Precondition Failed',
     '413': 'Payload Too Large',
     '414': 'URI Too Long',
     '415': 'Unsupported Media Type',
     '416': 'Range Not Satisfiable',
     '417': 'Expectation Failed',
     '418': 'I\'m a teapot',
     '421': 'Misdirected Request',
     '422': 'Unprocessable Entity',
     '423': 'Locked',
     '424': 'Failed Dependency',
     '425': 'Unordered Collection',
     '426': 'Upgrade Required',
     '428': 'Precondition Required',
     '429': 'Too Many Requests',
     '431': 'Request Header Fields Too Large',
     '451': 'Unavailable For Legal Reasons',
     '500': 'Internal Server Error',
     '501': 'Not Implemented',
     '502': 'Bad Gateway',
     '503': 'Service Unavailable',
     '504': 'Gateway Timeout',
     '505': 'HTTP Version Not Supported',
     '506': 'Variant Also Negotiates',
     '507': 'Insufficient Storage',
     '508': 'Loop Detected',
     '509': 'Bandwidth Limit Exceeded',
     '510': 'Not Extended',
     '511': 'Network Authentication Required' },
  Agent:
   { [Function: Agent]
     super_:
      { [Function: EventEmitter]
        EventEmitter: [Circular],
        usingDomains: true,
        defaultMaxListeners: [Getter/Setter],
        init: [Function],
        listenerCount: [Function] },
     defaultMaxSockets: Infinity },
  ClientRequest: { [Function: ClientRequest] super_: { [Function: OutgoingMessage] super_: [Object] } },
  globalAgent:
   Agent {
     domain:
      Domain {
        domain: null,
        _events: [Object],
        _eventsCount: 1,
        _maxListeners: undefined,
        members: [] },
     _events: { free: [Function] },
     _eventsCount: 1,
     _maxListeners: undefined,
     defaultPort: 80,
     protocol: 'http:',
     options: { path: null },
     requests: {},
     sockets: {},
     freeSockets: {},
     keepAliveMsecs: 1000,
     keepAlive: false,
     maxSockets: Infinity,
     maxFreeSockets: 256 },
  IncomingMessage:
   { [Function: IncomingMessage]
     super_:
      { [Function: Readable]
        ReadableState: [Function: ReadableState],
        super_: [Object],
        _fromList: [Function: fromList] } },
  OutgoingMessage:
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
        _uint8ArrayToBuffer: [Function: _uint8ArrayToBuffer] } },
  Server: { [Function: Server] super_: { [Function: Server] super_: [Object] } },
  ServerResponse: { [Function: ServerResponse] super_: { [Function: OutgoingMessage] super_: [Object] } },
  createServer: [Function: createServer],
  get: [Function: get],
  request: [Function: request] 
}
  ```

## HTTP简介
- `http`是一个对象。(Node.js的一个内置对象)
- 用于创建HTTP服务器。
- HTTP模块提供了一种方式，让Node.js可以通过http传输数据

## METHODS: http.createServer([options],[requestListener])
- 用途: 用于创建node服务器
- 参数: 
  - options:`object` 
    - 用途：指定接收消息的类
  - requestListener:`function`
    - 用途：自动添加到`request`事件上的处理函数。
- return: 新创建的`http.Server`实例

## CLASS:http.Server
- `net.Server`是另一个类，用于创建TCP或IPC服务器。
- `http.Server`继承自`net.Server` 用于创建http服务器
- server.request： 自有事件,只要有请求，就会触发request事件，每个connection可能会存在多个请求。
- server.setTimeout()
- server.close() : 关闭服务器连接
- server.listen() : 监听计算机端口
- server.listening : 检测服务器是否正在监听连接
```
{
  domain: null,
  _events: { connection: [Function: connectionListener] },
  _eventsCount: 1,
  _maxListeners: undefined,
  _connections: 0,
  _handle: null,
  _usingSlaves: false,
  _slaves: [],
  _unref: false,
  allowHalfOpen: true,
  pauseOnConnect: false,
  httpAllowHalfOpen: false,
  timeout: 120000,
  keepAliveTimeout: 5000,
  _pendingResponseData: 0,
  maxHeadersCount: null,
  [Symbol(asyncId)]: -1
}
```
server.__proto__
```
{
  setTimeout: [Function: setTimeout ]
}
```
server.__proto__.__proto__:
```
{
  _listen2: [Function: setupListenHandle],
  listen: [Function],
  listening: [Getter],
  address: [Function],
  getConnections: [Function],
  close: [Function],
  _emitCloseIfDrained: [Function],
  listenFD: [Function: deprecated],
  _setupSlave: [Function],
  ref: [Function],
  unref: [Function]
}
```

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





