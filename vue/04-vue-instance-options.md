# Vue Instance

- Vue实例是一个使用MVVM模式定义的ViewModel(视图模型)
- 当创建一个 Vue 实例时，你需要传入一个选项对象。选项用来创建你想要的行为。
  - el
  - data
- 每个 Vue 应用都是通过用 Vue 函数创建一个新的 Vue 实例开始的。

## 构建App从构建实例开始
```
const app = new Vue()
```
- 每个app都是从创建一个Vue实例开始。

## new Vue(options)
向实例传入选项
```
const app = new Vue({
  el: '#app',
  data: {
    key: 'value'
  }
})
```
- 一个Vue实例就是一个对象，里面保存了要管理的DOM和数据。只要数据发生变化，DOM就会自动更新。



## data:Vue实例的数据。
**data is an object**
```
new Vue({
  el: '#app',
  data: {
    firstName: 'Jay',
    lastName: 'Jordan'
  }
})
```
- Vue的data对象必须是纯粹的key/value对（只能是数据，不能有状态）
- Vue把data对象的属性转换为getter和setter，从而让data的属性能够响应数据的变化
- `vm.$data`用来访问原始data对象
- Vue实例代理了data对象的属性，所以`vm.key` = `vm.$data.key`

**data is a function when it used in a component**
```

```


## props:接收来自父组件的数据
**props is an Array**


**Porps is an Object**



## methods


## computed

## watch


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


## Components包含Vue实例可用组件的hashList

## filters包含Vue实例可用过滤器的hashList

## directive包含Vue实例可用指令的hashList




## Lifecycle

- `beforeCreate()`: `vm`实例初始化之后调用
  - `data`未获取
  - `computed`
  - `methods`
  - `watch`
  - `event`
- `created()`: `vm`实例创建完成之后调用
  - `data`已注入
  - `computed`已计算完成
  - `methods`已计算完成
  - `watch`事件回调
  - `event`事件回调
  - 挂载未开始，`vm.$el`不可见
- `beforeMount()`: `vm`渲染完毕(render()函数首次被调用),挂载之前调用
  - `vm.$el`已获取
- `mounted()`: `el`被`vm.$el`替换，并挂载到实例上去之后调用该钩子
  -  赋予你两种能力：1.访问template 2. interaction with the DOM
- `beforeUpdate()`: 数据更新时调用
- `updated()`: 数据更新后调用
- `activated()`: `<keep-alive>`组件激活时调用
- `deactivated()`: `<keep-alive>`组件停用时调用
- `beforeDestory()`: 实例销毁之前调用
- `destoried()`: 实例销毁之后调用
- `errorCaptured()`: 当捕获来自后代组件的错误时调用
