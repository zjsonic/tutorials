## express
- express是一个基于Node.js的web应用程序开发框架。
- express是一个顶级的请求处理函数。


## express()
- express()的返回值是一个`EventEmitter`对象

## app.use([path],callback,[callback])
- 用途：当路径匹配时 执行指定的中间件函数。
- path: string
- callback: middleware

## res.status(number)
- 用途：指定响应状态

## res.json([body])
- 用途：发送正文为JSON类型的HTTP响应。
- 使用JSON.stringify()把body转换为JSON字符串。
- body可以是任意json类型

## router.get()
- 用途：提供路由功能

## Express middleware (modules)
- morgan: HTTP 请求记录器
```
npm install --save morgan
```


## body-parser
```
npm install --save body-parser
```
- 用途:解析HTTP请求正文（在进入handler之前解析） parse the body of  the incoming request，默认的body格式不好，不容易读取
  - body-parser不支持文件，但支持url encoded body 和 json数据
  - 在中间件中解析传入的请求主体
  - 在处理程序之前解析
  - 在req.body属性下使用
- bodyParser.json([options])
 - 用途：返回只解析json并仅查看Content-Type标头与type选项匹配的请求的中间件。
 - 在中间件(即req.body)之后，将在请求对象上填充一个包含解析数据的新Body对象。
- bodyParser.urlencoded([options])
 - 用途：返回仅解析urlcodedbody并仅查看Content-Type标头与类型选项匹配的请求的中间件。




## 打印 express
```
{ [Function: createApplication]
  application: 
   { init: [Function: init],
     defaultConfiguration: [Function: defaultConfiguration],
     lazyrouter: [Function: lazyrouter],
     handle: [Function: handle],
     use: [Function: use],
     route: [Function: route],
     engine: [Function: engine],
     param: [Function: param],
     set: [Function: set],
     path: [Function: path],
     enabled: [Function: enabled],
     disabled: [Function: disabled],
     enable: [Function: enable],
     disable: [Function: disable],
     acl: [Function],
     bind: [Function],
     checkout: [Function],
     connect: [Function],
     copy: [Function],
     delete: [Function],
     get: [Function],
     head: [Function],
     link: [Function],
     lock: [Function],
     'm-search': [Function],
     merge: [Function],
     mkactivity: [Function],
     mkcalendar: [Function],
     mkcol: [Function],
     move: [Function],
     notify: [Function],
     options: [Function],
     patch: [Function],
     post: [Function],
     propfind: [Function],
     proppatch: [Function],
     purge: [Function],
     put: [Function],
     rebind: [Function],
     report: [Function],
     search: [Function],
     source: [Function],
     subscribe: [Function],
     trace: [Function],
     unbind: [Function],
     unlink: [Function],
     unlock: [Function],
     unsubscribe: [Function],
     all: [Function: all],
     del: [Function],
     render: [Function: render],
     listen: [Function: listen] },
  request: 
   IncomingMessage {
     header: [Function: header],
     get: [Function: header],
     accepts: [Function],
     acceptsEncodings: [Function],
     acceptsEncoding: [Function],
     acceptsCharsets: [Function],
     acceptsCharset: [Function],
     acceptsLanguages: [Function],
     acceptsLanguage: [Function],
     range: [Function: range],
     param: [Function: param],
     is: [Function: is],
     protocol: [Getter],
     secure: [Getter],
     ip: [Getter],
     ips: [Getter],
     subdomains: [Getter],
     path: [Getter],
     hostname: [Getter],
     host: [Getter],
     fresh: [Getter],
     stale: [Getter],
     xhr: [Getter] },
  response: 
   ServerResponse {
     status: [Function: status],
     links: [Function],
     send: [Function: send],
     json: [Function: json],
     jsonp: [Function: jsonp],
     sendStatus: [Function: sendStatus],
     sendFile: [Function: sendFile],
     sendfile: [Function],
     download: [Function: download],
     type: [Function: contentType],
     contentType: [Function: contentType],
     format: [Function],
     attachment: [Function: attachment],
     append: [Function: append],
     header: [Function: header],
     set: [Function: header],
     get: [Function],
     clearCookie: [Function: clearCookie],
     cookie: [Function],
     location: [Function: location],
     redirect: [Function: redirect],
     vary: [Function],
     render: [Function: render] },
  Route: [Function: Route],
  Router: 
   { [Function]
     param: [Function: param],
     handle: [Function: handle],
     process_params: [Function: process_params],
     use: [Function: use],
     route: [Function: route],
     acl: [Function],
     bind: [Function],
     checkout: [Function],
     connect: [Function],
     copy: [Function],
     delete: [Function],
     get: [Function],
     head: [Function],
     link: [Function],
     lock: [Function],
     'm-search': [Function],
     merge: [Function],
     mkactivity: [Function],
     mkcalendar: [Function],
     mkcol: [Function],
     move: [Function],
     notify: [Function],
     options: [Function],
     patch: [Function],
     post: [Function],
     propfind: [Function],
     proppatch: [Function],
     purge: [Function],
     put: [Function],
     rebind: [Function],
     report: [Function],
     search: [Function],
     source: [Function],
     subscribe: [Function],
     trace: [Function],
     unbind: [Function],
     unlink: [Function],
     unlock: [Function],
     unsubscribe: [Function],
     all: [Function] },
  json: [Function: json],
  query: [Function: query],
  static: 
   { [Function: serveStatic]
     mime: 
      Mime {
        types: [Object],
        extensions: [Object],
        default_type: 'application/octet-stream',
        Mime: [Function: Mime],
        charsets: [Object] } },
  urlencoded: [Function: urlencoded] }
  ```

  ## 打印express()
  ```
  { [EventEmitter: app]
  domain: undefined,
  _events: { mount: [Function: onmount] },
  _maxListeners: undefined,
  setMaxListeners: [Function: setMaxListeners],
  getMaxListeners: [Function: getMaxListeners],
  emit: [Function: emit],
  addListener: [Function: addListener],
  on: [Function: addListener],
  prependListener: [Function: prependListener],
  once: [Function: once],
  prependOnceListener: [Function: prependOnceListener],
  removeListener: [Function: removeListener],
  removeAllListeners: [Function: removeAllListeners],
  listeners: [Function: listeners],
  listenerCount: [Function: listenerCount],
  eventNames: [Function: eventNames],
  init: [Function: init],
  defaultConfiguration: [Function: defaultConfiguration],
  lazyrouter: [Function: lazyrouter],
  handle: [Function: handle],
  use: [Function: use],
  route: [Function: route],
  engine: [Function: engine],
  param: [Function: param],
  set: [Function: set],
  path: [Function: path],
  enabled: [Function: enabled],
  disabled: [Function: disabled],
  enable: [Function: enable],
  disable: [Function: disable],
  acl: [Function],
  bind: [Function],
  checkout: [Function],
  connect: [Function],
  copy: [Function],
  delete: [Function],
  get: [Function],
  head: [Function],
  link: [Function],
  lock: [Function],
  'm-search': [Function],
  merge: [Function],
  mkactivity: [Function],
  mkcalendar: [Function],
  mkcol: [Function],
  move: [Function],
  notify: [Function],
  options: [Function],
  patch: [Function],
  post: [Function],
  propfind: [Function],
  proppatch: [Function],
  purge: [Function],
  put: [Function],
  rebind: [Function],
  report: [Function],
  search: [Function],
  source: [Function],
  subscribe: [Function],
  trace: [Function],
  unbind: [Function],
  unlink: [Function],
  unlock: [Function],
  unsubscribe: [Function],
  all: [Function: all],
  del: [Function],
  render: [Function: render],
  listen: [Function: listen],
  request: IncomingMessage { app: [Circular] },
  response: ServerResponse { app: [Circular] },
  cache: {},
  engines: {},
  settings: 
   { 'x-powered-by': true,
     etag: 'weak',
     'etag fn': [Function: generateETag],
     env: 'development',
     'query parser': 'extended',
     'query parser fn': [Function: parseExtendedQueryString],
     'subdomain offset': 2,
     'trust proxy': false,
     'trust proxy fn': [Function: trustNone],
     view: [Function: View],
     views: '/Users/zj/my-projects/node-rest-shop/views',
     'jsonp callback name': 'callback' },
  _eventsCount: 1,
  locals: 
   { settings: 
      { 'x-powered-by': true,
        etag: 'weak',
        'etag fn': [Function: generateETag],
        env: 'development',
        'query parser': 'extended',
        'query parser fn': [Function: parseExtendedQueryString],
        'subdomain offset': 2,
        'trust proxy': false,
        'trust proxy fn': [Function: trustNone],
        view: [Function: View],
        views: '/Users/zj/my-projects/node-rest-shop/views',
        'jsonp callback name': 'callback' } },
  mountpath: '/',
  _router: 
   { [Function: router]
     params: {},
     _params: [],
     caseSensitive: false,
     mergeParams: undefined,
     strict: false,
     stack: 
      [ [Object],
        [Object],
        [Object],
        [Object],
        [Object],
        [Object],
        [Object],
        [Object],
        [Object],
        [Object],
        [Object] ] } }
```