# Core Module: HTTP
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


## 内置模块：HTTP

- `http`是一个对象。
- 用于创建HTTP服务器。
- HTTP模块提供了一种方式，让Node.js可以通过http传输数据
```
{
  _connectionListener: [Function: connectionListener],
  METHODS: [],
  STATUS_CODES: {},
  Agent: {},
  Server: {},
  ServerResponse: {},
  createServer: [Function: createServer],
  get: [Function: get],
  request: [Function: request]
}
```

## http.createServer()
```
const server = http.createServer(function(req,res){

})
```
- 用途: 用于创建一个 `Server`对象
- 参数: 
  - options object:指定要使用的接收消息的类
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