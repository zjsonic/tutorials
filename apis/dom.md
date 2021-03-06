# DOM Basic

## What is the DOM?
- DOM是Document Object Model的缩写,翻译为"文档对象模型".
- DOM是基于HTML文档编写程序的接口.
  - 修改文档结构
  - 修改文档样式
  - 修改文档内容
- DOM把一个文档描述为`Nodes`和`Objects`,这样就把一个文档和脚本语言连接起来了.
- js使用DOM访问文档和文档元素


## 如何访问DOM
- 把脚本嵌入`<script></script>`内
- 把脚本编写在一个外部文件,然后使用`<script src='my.js'></script>`引入脚本文件
以上两种方法均可以让你立刻使用API操作DOM文档.


## 数据类型
- Document: this object is the root document
- Element: element refers an element or an node of the type element
- NodeList: It is an array of elements.
- Attribute: 它是一个对象引用, 它为了attribute暴露了一个特殊的接口.
- NamedNodeMap:


## DOM Interfaces 核心
document.getElementById(id)
document.getElementsByTagName(name)
document.createElement(name)
parentNode.appendChild(node)
element.innerHTML
element.style.left
element.setAttribute()
element.getAttribute()
element.addEventListener()
window.content
window.onload
window.dump()
window.scrollTo()


# Document Interface

## `document`对象是访问页面内容(DOM树)的入口
```
console.log(document)
```

## `Document()`构造函数用于创建新文档对象
- 参数: 无
-
```
const doc = new Document()
```


## document.anchors
- 用途:返回文档中所有带name属性的anchors(注意:不返回带id属性的a)
- 返回值: `HTMLCollection` interface(类数组:元素的集合)








## DOM元素树

```
alert(document) // HTMLDocument
alert(document.documentElement) // HTMLHtmlDocument

alert(document.documentElement.childNodes) // NodeList
alert(document.documentElement.childNodes.length) // 3
alert(document.documentElement.childNodes[0]) // HTMLHeadElement
alert(document.documentElement.childNodes[0].childNodes) // 9
alert(document.documentElement.childNodes[0].childNodes[0]) //Text
alert(document.documentElement.childNodes[0].childNodes[1]) // HTMLMetaElement
alert(document.documentElement.childNodes[0].childNodes[7]) // HTMLTitleElement
alert(document.documentElement.childNodes[0].childNodes[7].firstChild.nodeValue) // 'Document'
alert(document.documentElement.childNodes[1]) // Text
alert(document.documentElement.childNodes[2]) // HTMLBodyElement

alert(document.forms) // HTMLCollection
alert(document.forms.myForm1) //HTMLFormElement

// alert(document.images) // HTMLCollection
// alert(document.images.length)  //2

alert(document.links) //HTMLCollection
alert(document.links.length) //只返回包含href属性的a链接


```


# Event类
- `Event`类是一个浏览器的API.
- 每个事件都是继承自`Event`类的对象
- `Event`接口表示DOM中发生的事件.

## 什么是事件？
事件不是什么技术名词。简单说 **事件就是浏览器窗口内发生了什么事**。这些事件的产生来自:
- 用户产生的事件
- API(浏览器)产生的事件
在终端用户和页面交互的时候，事件经常被触发。比如:
* 用户在窗口内移动鼠标，鼠标事件就被用户触发了;
* 当用户在键盘上敲击文字，键盘事件就被触发了；
* 当用户在表单中录入文字时，表单事件就被触发了。


## 事件类型
**事件类型就是表示事件名称的一个字符串**
当浏览器窗口内发生某个事件时，浏览器要通知JavaScript程序，发生了什么事，这时候，事件必须有个名字,这个名字就是事件类型(事件名称).
-  `mouseover`:表示用户移动鼠标。
- `keydown`：表示键盘上某个键被按下。
- `load`：表示文档从网络上加载完毕。

## 事件目标
**事件目标就是产生事件的主体对象**
当浏览器窗口内发生某个事件的时候,浏览器除了要通知js程序,发生了什么事,还要告诉js程序,这个事件是哪个对象发出的. 也就是说,只要在 JavaScript中提及事件的时候，必须同时指明事件类型和事件目标：
- window上的load事件
- `<button>`元素上的click事件
- `<input>`元素上的board事件

## 事件处理程序
**事件处理程序就是处理事件的函数。**
当浏览器内某个元素上发生了某个事件时，你希望做些什么？比如：
- 当文档加载完毕后，你希望弹出一个广告？
- 打开窗口弹出一个对话框
- 当鼠标点击按钮后，你希望提交一个表单？
- 当点击一个点击一个按钮时，数字能自动加1
你把你希望它做的事情写成一个函数，当窗口内发生某个事件时调用你写的函数。这个函数就是事件处理程序。

## 为DOM元素注册事件处理程序的三种方法
- 通过DOM元素的方法: EventTarget.addEventListener('eventName',function,[false])
  - 优点：可以为事件对象的事件类型注册多个处理程序。
  - 缺点：IE9以下的浏览器不支持该方法。
- 通过DOM元素的属性: EventTarget.onEventName
  - 优点：适用所有浏览器和所有常见事件类型。
  - 缺点：事件目标上的事件类型只能有一种事件处理程序。
- 通过HTML元素的属性
  - 优点：适用所有浏览器。
  - 缺点：内容和行为不分离。
- `attacheEvent('oneventName',function)` (不支持冒泡）
  - 优点：可以为事件对象的事件类型注册多个处理程序。
  - 缺点：IE9以下的浏览器不支持该方法。


## 事件处理程序的兼容写法
```
var b = document.getELementById('myid');
var fn = function(){
    alert('thanks');
}
if(b.addEventListener){
    b.addEventListen('click',fn,false);
} else if(b.attachEvent){
    b.attachEvent('onclick',fn);
};
```

## readystatechange(值改变)
- specifics: HTML5 和 XMLHTTPRequest
- 触发:当document对象的`readyState`属性值改变时
- 触发:当XMLHTTPRequest对象的`readyState`状态改变时
- `document.readyState`描述了文档的加载状态
  - `loading` :文档正在加载
  - `interactive`: 文档的直接资源已经加载完成,子资源(图片,stylesheet,iframe等)正在加载
  - `complete`: 直接资源和子资源全部加载完成,`load`事件即将触发
- `XMLHTTPRequest.readyState`描述请求对象的状态
  - `UNSENT` = 0 : open()未调用
  - `OPENED` = 1 : open()已调用
  - `HEADERS_RECEIVED` = 2 : 接收到响应头
  - `LOADING` = 3 : 接收到响应主体
  - `DONE` = 4 : 响应完成
```
document.onreadystatechange = () => {
  console.log(document.readyState)
}
```

## load(资源加载)
- 触发:资源及其依赖的资源加载完成时触发
- 常见的资源加载:
 - window.onload
 - script.onload
 - link.onload
 - imgage.onload
 - XMLHTTPRequest.onload
