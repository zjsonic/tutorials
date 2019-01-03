# Components

- What is component
- Component Registration on Vue()
- Component Registration on new Vue()
- Single File Component
-

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

**在Vue实例中引入组件**
```
new Vue({
  el: '#app',
  components: {
    'component-a': ComponentA,
    'component-b': ComponentB
  }
})
```

## 通过props向子组件传递数据
- props是创建组件的数据选项
- 基本用法：
  - props在组件类中定义
  - props在组件实例上注入数据
  - props在组件类中接收数据
  - props可以是数组，也可以是对象。



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



## 动态组件

## `<component>`

## 通过`<slot>`分发内容
- 用于标记往哪个具名插槽中插入子组件的内容

## `<transition>`

## `<keep-alive>`
