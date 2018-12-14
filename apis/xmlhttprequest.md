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




# HTTP


## 什么是web
web是指World Wide Web(万维网)，万维网是由HTML、URL、HTTP构成的分布式系统。
- HTML构建超文本文档的语言
- URL:统一资源定位符，可以定位该资源
- URI:统一资源标识符，可以标识该资源
- HTTP超文本转移协议（主要为了解决文本传输的难题）

URI的标准格式：
```
http://user:pass@www.domain.com:80/dir/index.html?id=1#ch1
```
- `http`:协议方案名
- `user:pass` : 登录信息
- `www.domain.com` : 服务器地址
- `80`: 服务器端口号
- `dir/index.html` : 带层次的文件路径
- `id=1` : 查询字符串
- `ch1` : 片段标识符

## 什么是HTTP

**HTTP用于客户端和服务器端之间的通信**
- 客户端：协议规定了客户端如何向服务端请求资源、发送资源。
- 服务端：协议规定了服务端如何响应客户端（服务端必须回复响应）。

**HTTP的发展**
- 1996年5月 `HTTP`作为标准被公布，版本`HTTP/1.0`
- 1997年1月 `HTTP/1.1`公布，是目前主流的HTTP版本
- 2018年11月 HTTP/2.0仍在制定中

## 请求报文

`POST` `/form/entry` `HTTP/1.1`  

`Host: hackr.jp
Connection: keep-alive
Content-Type: application/x-www-form-urlencoded
Content-Length: 16
`

`name=ueno&age=20`

- 请求报文首部
  - 请求行
    - 请求的方法：`GET` `POST` `HEAD` `PUT`等
    - 请求的URI：
    - HTTP版本：`HTTP/1.1`
  - 请求首部字段
    - `Accept`:用户代理可处理的媒体类型
    - `Referer`: 对请求中URI的原始获取方
    - `User-Agent`:用户代理信息
  - 通用首部字段(General Header Fields):请求报文和响应报文都会使用的首部
    - `Cache-Control`:控制缓存的行为
    - `Date`:创建报文的日期时间
    - `Transfer-Endoding`: 指定报文主体的传输编码方式
  - 请求实体首部字段
    - `Cache-Control`:控制缓存的行为
    - `Content-Encoding`:实体主体的编码方式
    - `Content-Language`:实体主体的语言
    - `Content-Length`:实体主体的大小
    - `Content-Type`:`type/subtype` (描述实体主体的媒体类型。MIME:支持非ASCII字符支持非文本字符)
      - text:
        - `text/plain`（纯文本）
        - `text/html`（html文档）
      - `image`:
        - `image/gif`
        - `image/png`
        - `image/jpeg`
      - `video`:
      - `audio`:
      - `application`:传输应用程序数据 或 二进制数据
        - `application/xhtml-xml`(xhtml文档)
        - `application/pdf`
        - `application/msword`
        - `application/x-www-form-urlencoded`(使用POST方法提交的表单)
      - `multipart`:用于传输多种类型的数据
        - `multipart/form-data` (适用于提交表单时伴随文件上传)
    - `Expires`: 实体主体的过期日期
    - `Last-Modified`: 资源的最后修改日期
- 请求报文主体


## 响应报文
`HTTP/1.1` `200` `OK`

`Date: Tue,10 Jul 2018 09:50:20 GMT
 Content-Length: 362
 Content-Type: text/html
`

`<html>...`
- 响应报文首部
  - 状态行
    - 协议版本: `HTTP/1.1`
    - 状态码：HTTP状态码可描述请求的处理结果
      - 1xx:正则处理请求
      - 2xx: 请求成功处理完毕。
      - 3xx: 重定向以完成请求
      - 4xx: 服务器无法处理请求
      - 5xx: 服务器处理请求出错
    - 状态说明：文字说明  如：'OK'
  - 响应首部字段
    - `Accept-Ranges`: 是否接受字节范围请求
  - 通用首部字段(General Header Fields):见上
  - 响应实体首部字段：见上
- 响应报文主体

## HTTP解析
**HTTP是不保存状态的协议**

为了更快的处理大量事物，特意把HTTP设计的如此简单。协议本身不保留之前一切的请求报文或相应报文。为了实现保持状态的功能，引入了Cookie技术。

**使用URI定位资源**

- 正是因为URI的特定功能，在互联网上任意位置的资源都能访问到。
- 当客户端发送请求时，需要将URI包含在请求报文中
- 指定请求URI的方式很多

**告知服务器意图的方法**

- GET :  获取资源
- POST : 传输实体主体
- PUT : 传输文件（自身没有验证机制）
- HEAD: 获得报文首部
- DELETE: 删除文件
- OPTIONS: 询问支持的方法
- TRACE: 追踪路径
- CONNECT: 要求用隧道协议连接代理



## HTTP状态码


## web服务器


## HTTP首部

## HTTPS

## 身份认证

## 追加协议

## 构建web内容的技术

## web的攻击技术
