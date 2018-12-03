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

