## HTTP


## XMLHttpRequest是一个挂载在window对象上的方法
```
  console.log(window.XMLHttpRequest)
  console.log(XMLHttpRequest)
```

## XMLHttpRequest是一个构造函数
使用XMLHttpRequest，从创建实例开始
```
const request = new XMLHttpRequest
```
该实例的原型上有许多方法
```
console.log(request)
console.log(request.hasOwnProperty('open')) // false
console.log(request.__proto__.hasOwnProperty('open')) //true
```

## XMLHttpRequest的方法
- request.open(method,url,blean)
- request.send(string)


## XMLHttpRequest的属性

- request.readyState : 该属性中存储着XMLHttpRequest对象的状态
  - `0` : request请求尚未初始化
  - `1` : 服务器连接建立
  - `2` : 收到请求
  - `3` : 处理请求中
  - `4` : 请求已完成，响应已就绪
- request.onreadystatechange : 事件属性。该属性用于监听XMLHttpRequest对象的状态的变化
- request.status : 该属性存储着服务端返回的HTTP的状态信息码 ([查看状态码详情](https://www.w3schools.com/tags/ref_httpmessages.asp))
- request.statusText : 该属性存储着服务端返回的HTTP的状态信息字符串


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















## JQurey


## Promise是什么

- `Promise`是一个原生构造函数，用于生成promise实例。
- `Promise()`构造函数接受一个函数参数。
  - 该函数的内部包括的是一个异步操作
  - 该函数的参数是两个内置的方法: resolved()  rejected()
    - resolved的作用是将promise对象的状态从pending变成resolved
    - rejected的作用是将proised对象的状态从pending变成rejected
- 缺点：无法中途取消，一旦创建它就会立刻执行

## promise.then(fb1,fb2)

then方法用来指定promise实例的回调函数：
- fb1: 在pending变为resolved时调用
- fb2: 在pending变为rejected时调用
```
promise.then(function(value){

},function(error){

})
```



## Generator

## async



## Axios是什么

Axios是一个函数。可用于创建HTTP请求。支持浏览器和Node.js,自动转换JSON数据。


## axios()/AxiosAPI
使用axios创建http请求，只需向其传入相关配置即可。
- axios({config})
```
axios({
  method:'post',
  url: '/usr/123',
  data: {
    firstName: 'zhang',
    lastName: 'Jie'
  }
})

```
- axios(url,{config})
```
axios('/usr/123')
```





## 请求配置

## 响应结构

## 配置的默认值

## 拦截器

## 错误处理

## 取消





## fetch


## firebase install

```
$ npm install firebase-tools -g
```
## initialize project
```
$ cd project
$ firebase init hosting
```
