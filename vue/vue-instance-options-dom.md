# DOM Options

## Vue使用的模板语言
- 模板语言是HTML的超集。任何HTML都是有效的Vue.js的模板。
- 模板将会被Vue编译后生成的DOM所替换。

## el: 提供一个页面上已知的DOM元素作为Vue实例的模板。
- 语法： `el:'CSSSelector'|HTMLElement `

CSSSelector: css选择器(string)
```
new Vue({
  el: ‘#app’
})

```
HTMLElement: 一个DOM元素节点
```
new Vue({
  el: document.querySelector('#app')
})
```
## template:提供一个字符串模板作为Vue实例的模板
- 语法： `template: 'string'`
- 若存在el,则el将会被模板替换。(除非模板的内容有分发插槽)
- 若不存在el,则。。。。。
- 绝大多数情况下使用 template 来创建你的 HTML

el将会被模板替换
```
new Vue({
  el: '#app',
  template: '<h2>{{ msg }}</h2>',
  data: {
    msg: 'Hello World!'
  }
})
```

## render: render(createElement,[context]):使用函数创建Vue实例的模板
- createElement(): 创建VNode，返回值：VNode
- context: 为无实例的组件提供上下文
```
待补充
```
