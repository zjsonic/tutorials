# Components

- What is component
- Component Registration
  - Component Registration on Vue()
  - Component Registration on new Vue()
  - Component Registration in a Module System
- Passing Data
  - Passing data to Child Component with props
  - Sending message to Parents with event
  - Content Distribution with slot
- Built-In Components
  - `<component>`：元组件、动态组件
  - `<slot>`: 插槽
  - `<keep-alive>`: 保留组件状态
  - `<transition>`:
- Asynchronous Components
- Handle Edge Cases
  - Accessing the Instance
    - Access the root instance
    - Access the parent instantce
    - Access the child instance
  - Manually listen for events on component instance
  - Circlar References
  - inline-template & x-template
  - Controlling Updates
## What is component
- 组件是可复用的Vue实例。
- 组件可以当做自定义元素来使用。

## Component Registration on Vue()

**标准语法**

```
Vue.component('id',Vue.extend({ options }))
```
- id: string 指定组件名称
- Vue.extend(): 构造器。创建Vue构造函数的“子类”(子构造函数)。
  - options: 选项对象
    - data: 必须是函数
- Vue.extend()的实例：组件的每一次应用，组件实例会被自动创建

**简洁语法**
```
Vue.component('id',{ options }) //自动调用Vue.extend构造器
```
**案例**
```
<div id="app">
  <my-component></my-component>
  <my-component></my-component>
  <my-component></my-component>
</div>
<script type="text/javascript">
  new Vue({ el: '#app' })
  Vue.component('my-component',{
    data: function(){
      return {
        count: 0
      }
    },
    template: '<h1 v-on:click="getCount"> {{ this.count }} </h1>',
    methods: {
      getCount: function(){
        return this.count++
      }
    }
  })
</script>

```
上述代码会报错：
>[Vue warn]: Unknown custom element: <my-component> - did you register the component correctly? For recursive components, make sure to provide the "name" option.

原因：
- `my-component`组件是通过`Vue()`构造函数的Vue.extend({options})方法注册的，为了简洁，Vue.extend()省略没写。
- 在实例化时，遇到`el`会立刻进入编译过程，但此刻并未编译子类。
- 在构造函数Vue()还未注册组件之前进行实例化显然是错误的。

解决：
- 方法1：把实例化代码`new Vue({ el: '#app' })`放在组件注册之后
- 方法2：在实例化选项内，显示声明Vue实例可用组件
```
new Vue({
    el: '#app',
    components: {
      'my-component': my-component
    }
})
```

## Component Registration on new Vue()

**全局注册有缺点**
在webpack这样的打包系统中，全局注册的代码会最终包含在最终的构建结果中，造成代码无谓增加。

**使用普通js对象的语法定义组件**

```
var ComponentA = { /* ... */ }
var ComponentB = { /* ... */ }
var ComponentC = { /* ... */ }
```

**在Vue实例中注册组件**
```
new Vue({
  el: '#app',
  components: {
    'component-a': ComponentA,
    'component-b': ComponentB
  }
})
```
## Component Local Registration in a Module System
singfile.js or singfile.vue
```
import 'component-a' from './components/component-a'

export default {
  components: {
    `component-a`: component-a
  }
}
```
## 通过props向子组件传递数据
- props是创建组件的数据选项
- 基本用法：
  - props在组件类中定义
  - props在组件实例上注入数据
  - props在组件类中接收数据
  - props可以是数组，也可以是对象。
- props大小写问题
  - HTML的属性不区分大小写
  - 所以浏览器会把大写属性解析成小写
  - 所以在内嵌DOM模板中，camelCased需要换成kebab-cased
  - 注意：字符串模板不受此限制
- props的类型

## Component Global Registration of Basic Components In a Module System
**基本组件**:指通常只包含一个元素的基本的、通用的组件。
- 使用`require.context()`注册
```
const requireComponent = require.context(
  // The relative path of the components folder
  './components',
  // Whether or not to look in subfolders
  false,
  // The regular expression used to match base component filenames
  /Base[A-Z]\w+\.(vue|js)$/
)
```

## 通过vm.$emit(eventName,[...args])向父组件传递消息
- `vm.$emit()`是实例的方法。`vm.$emit()`用于触发组件实例上定义的事件。
- 基本用法：
  - 在组件实例上使用`v-on`监听自定义事件
  - 在组件类中通过事件触发`$emit()`

- 参数用法
  - 通过参数抛出一个值
  - 如果该值会作为第一个参数传入事件处理函数
- 在input上使用`v-model`监听事件
  - 将组件的`value`特性绑定到一个名叫`value`的prop上
  - 在组件的`input`事件被触发时，将新的值通过自定义的`input`事件抛出


```
<button v-on:click ="$emit('enlarge-text', 0.2)"
```
- `0.2`会自动作为第一个参数传入事件处理函数



## 异步组件
**基本用法：以工厂函数的方式定义组件**

```
Vue.component('async-example', function (resolve, reject) {
  setTimeout(function () {
    // 向 `resolve` 回调传递组件定义
    resolve({
      template: '<div>I am async!</div>'
    })
  }, 1000)
})

```

**推荐用法：将异步组件和require()配合使用**

```
Vue.component('async-webpack-example', function (resolve) {
  // 这个特殊的 `require` 语法将会告诉 webpack
  // 自动将你的构建代码切割成多个包，这些包
  // 会通过 Ajax 请求加载
  require(['./my-async-component'], resolve)
})
```

**ES6用法：箭头函数+import+Promise**

```
Vue.component(
  'async-webpack-example',
  // 这个 `import` 函数会返回一个 `Promise` 对象。
  () => import('./my-async-component')
)
```

**局部注册：直接返回一个promise**
```
new Vue({
  // ...
  components: {
    'my-component': () => import('./my-async-component')
  }
})
```

## `<component>`
- `<component>`是“元组件”。
- `<component>`用于渲染动态组件。
- `<component>`依据`is`的值决定渲染哪个组件

## 通过`<slot>`显示组件实例的内容
- 组件实例的内容可以是纯文本，也可以是HTML内容。
- `<slot>`自身将被组件实例的内容替换。

## `<transition>`

## `<keep-alive>`
- 组件是有状态的
- `<keep-alive>`用于保留组件状态
- `<keep-alive>`是一个抽象组件，不会被渲染DOM。
