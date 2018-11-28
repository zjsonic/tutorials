# Core Module: HTTP
- 打印HTTP
- HTTP简介
- class
    - http.Agent
    - http.ClientRequest
    - http.Server
    - http.ServerResponse
    - http.IncomingMessage
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

## http.createServer([options],[requestListener])
- 用途: 用于创建node服务器
- 参数: 
  - options: 指定要使用的接收消息的类
    - 类型： object
    - IncomingMessage
    - ServerResponse
  - function:requestListener(req,res) 请求监听函数
    - 每次服务器收到一个请求就会执行requestListener()函数
    - requestListener()处理用户请求也响应用户请求
    - req: 表示`IncomingMessage`对象（请求对象），该对象有处理请求的方法
      - req.url
      - req.method
      - req.headers
      - req.statusCode
    - res: 表示`ServerResponse`对象(响应对象,返回客户端的可写流)，该对象有处理响应的方法
      - res.writeHead(200,{ 'Content-Type': 'text/plain' }): 发送状态和响应头给客户端
      - res.write( req.url ): 发送文本给客户端
      - res.end(): 响应已完成的信号
      - getHeader()
      - setHeader()
- return: `http.Server`(function)

## Server对象
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