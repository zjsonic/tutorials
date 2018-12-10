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
