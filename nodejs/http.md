[TOC]

# HTTP

- `http` module is a built-in module in node.js.
- `http` module is an object.
- `http` module implements support for the HTTP. In other words, it allows node.js  to transfer data over HTTP.

```javascript
{ _connectionListener: [Function: connectionListener],
  METHODS:
   [ 'ACL',
     'BIND',
     'CHECKOUT',
     'CONNECT',
     'COPY',
     'DELETE',
     'GET',
     'HEAD',
     'LINK',
     'LOCK',
     'M-SEARCH',
     'MERGE',
     'MKACTIVITY',
     'MKCALENDAR',
     'MKCOL',
     'MOVE',
     'NOTIFY',
     'OPTIONS',
     'PATCH',
     'POST',
     'PROPFIND',
     'PROPPATCH',
     'PURGE',
     'PUT',
     'REBIND',
     'REPORT',
     'SEARCH',
     'SOURCE',
     'SUBSCRIBE',
     'TRACE',
     'UNBIND',
     'UNLINK',
     'UNLOCK',
     'UNSUBSCRIBE' ],
  STATUS_CODES:
   { '100': 'Continue',
     '101': 'Switching Protocols',
     '102': 'Processing',
     '103': 'Early Hints',
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
     '418': 'I\'m a Teapot',
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
        usingDomains: false,
        defaultMaxListeners: [Getter/Setter],
        init: [Function],
        listenerCount: [Function] },
     defaultMaxSockets: Infinity },
  ClientRequest:
   { [Function: ClientRequest] super_: { [Function: OutgoingMessage] super_: [Function] } },
  globalAgent:
   Agent {
     _events: [Object: null prototype] { free: [Function] },
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
        super_: [Function],
        _fromList: [Function: fromList] } },
  OutgoingMessage:
   { [Function: OutgoingMessage]
     super_:
      { [Function: Stream]
        super_: [Function],
        Readable: [Function],
        Writable: [Function],
        Duplex: [Function],
        Transform: [Function],
        PassThrough: [Function],
        pipeline: [Function: pipeline],
        finished: [Function: eos],
        Stream: [Circular],
        _isUint8Array: [Function: isUint8Array],
        _uint8ArrayToBuffer: [Function: _uint8ArrayToBuffer] } },
  Server:
   { [Function: Server] super_: { [Function: Server] super_: [Function] } },
  ServerResponse:
   { [Function: ServerResponse] super_: { [Function: OutgoingMessage] super_: [Function] } },
  createServer: [Function: createServer],
  get: [Function: get],
  request: [Function: request],
  maxHeaderSize: [Getter] }
```

## http暴露的接口

- class
  - http.Server():  用来实例化一个http server
  - http.ClientRequest(): 用来实例化一个http请求
  - http.ServerResponse(): 用来实例化一个http响应
  - http.IncomingMessage(): 用来实例化一个请求信息对象
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

## Class: http.Server

`http.Server` is used to create an server instance.

- `http.Server` inherits from `net.Server` which class is used to create a TCP/IP server instance.

Create an instance of `http.Server` class:

```javascript
const http = require('http')
const server = new http.Server

server.on('request',function(){
    console.log('request event occurs')
})
server.on('connection',function(){
    console.log('connection event occurs')
})
server.on('close',function(){
    console.log('close event occurs')
})

server.listen(3000)
```

### server event: request

Emitted each time there is a request.

- Request: `<http.IncomingMessage>` 
- Response: `<http.ServerResponse>` 

### server.listen()

## http.createServer(`[options]` `[,requestlistener]`) 

`http.createServer` returns a new instance of `http.Server` .  

- Options: `<object>` 
  + IncomingMessage:
  + ServerResponse:
- requestListener: `<function>` 
- Returns: `<http.Server>` 

Its source code in node.js below: 

```javascript
function createServer(opts, requestListener) {
  return new Server(opts, requestListener);
}
```

[https://github.com/nodejs/node-v0.x-archive/blob/master/lib/http.js#L1674](https://github.com/nodejs/node-v0.x-archive/blob/master/lib/http.js#L1674)

Create a server with `http.createServer` :

```javascript
const http = require('http')
const server = http.createServer((request,response) => {
    console.log(request)
}).listen(3000) // The server object returned by createServer function is actually an EventEmitter
```

## Class: http.IncomingMessage

`http.IncomingMessage` is used to create an request instance.

- The `incomingMessage` object is created by `http.Server` , when the `request` event is fired.
- The `incomingMessage` object is passed as the first argument to the `requestListener` function.

```javascript
const http = require('http')
http.createServer((req,res) => {
  res.end(req.url)
})
```

### im.url

Returns the request URL string.

### im.method

Returns the request method.

### im.headers

Returns an object containing header names and values.

### im.rawHeaders

Returns an array of the request headers.

## Class: http.ServerResponse

`http.ServerResponse` is used to create an response(a writable steam back to the client) instance. 

- The serverResponse object is created internally by an HTTP server - not by the user.
- The serverResponse object is passed as the second argument to the `requestListener` function.

```javascript
const http = require('http')
http.createServer(function(req,res){
  res.writeHead(200,{"content-type":"text/plain"})
  res.write('Hello World')
  res.end()
})
```

### sr.end()

### sr.getHeader()

### sr.setHeader()

### sr.write()

### sr.writeHead()

Sends status and response headers to the client.














