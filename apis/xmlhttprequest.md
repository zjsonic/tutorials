## AJAX
- Asynchronous JavaScript and XML
- 术语AJAX描述了一种主要使用脚本操作HTTP的web应用框架
- 主要特点：不会导致页面重载
- 实现AJAX的方式有多种：
  - 使用脚本操作`<img>`标签的`src`属性时，浏览器会发起HTTP GET请求，把经过编码的数据作为URL的查询字符串传递给服务器。特点：数据交换是单向的，客户端能发送数据到服务器，但服务器返回的只是一张1*1像素的透明图片。
  - `<iframe>`：首先把数据编码到URL中，然后设置`<iframe>`的src属性为该url，服务器能创建一个包含响应内容的HTML文档，并返回给客户端，缺点：受限于同源策略问题。
  - `<script>`: 该标签的src属性能设置URL并发起HTTP GET请求。可以跨域通信。服务器的响应采取JSON的数据格式，当执行脚本时，js解析器能自动将其解码，因此这种AJAX传输协议也叫`JSONP`
  - 所有浏览器都支持`XMLHttpRequest`对象，能实现get请求，也能实现post请求


## XMLHttpRequest类
浏览器在XMLHttpRequest类上定义了它们的HTTP API,使用HTTP API首先要实例化：
```
const request = new XMLHttpRequest
```
- 每个实例都代表一个独立的请求/响应对
- 该实例的原型上有许多方法
- XMLHttpRequest通常异步使用(发送请求后，send()方法立即返回，直到响应返回，响应的方法和属性才有效。必须监听readystatechange事件)
```
console.log(request.hasOwnProperty('open')) // false
console.log(request.__proto__.hasOwnProperty('open')) //true
```
## HTTP请求的构成
- 请求方法:第一到达
- 请求地址：第二到达
- 请求头(可选)：第三到达
- 请求主体()：第四到达

## HTTP响应的构成
- 响应状态（成功或失败）
- 响应头
- 响应主体

## XMLHttpRequest的方法
- request.open(method,url,async,usr,pw)
  - method: GET POST DELETE HEAD OPTIONS  PUT
  - URL: 相对url或绝对url(协议、主机、端口必须和当前文档对应的内容匹配)
- request.setRequestHeader()
  - `Content-Length`
  - `Date`
  - `Referer`
  - `User-Agent`
  - `Authorization`
  - `Content-Type`:POST请求拥有主体时，需要指定content-type
- request.send(string)
- request.getResponseHeader() 查询响应头
- request.getAllReponseHeaders()



## XMLHttpRequest的属性

- `request.readyState` : 查询XMLHttpRequest对象的状态
  - `0` : request请求尚未初始化
  - `1` : 服务器连接建立
  - `2` : 收到请求
  - `3` : 处理请求中
  - `4` : 请求已完成，响应已就绪
- `request.onreadystatechange` : XMLHttpRequest对象的监听程序
- `request.status` : 查询服务端返回的HTTP的状态信息(数字码) ([查看状态码详情](https://www.w3schools.com/tags/ref_httpmessages.asp))
- `request.statusText` : 查询服务端返回的HTTp状态信息（字符串）
- `request.responseText`
- `request.responseXML`

## 使用get请求数据
写一个函数，对于不同apiUrl，可以获取到数据，并对数据进行处理，参数如下：
- url : api url
- handler:使用不同方式处理获取到的数据




//第一步：创建请求

//第二步：设置请求

//第三步：发送请求

//第四步：接收响应

```
XMLHttpRequest()构造函数

- request.open()
- request.setRequestHeader()
- request.send()
- request.readyState
- request.status
- request.onreadystatechange
- request.reponseText
