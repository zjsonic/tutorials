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
