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
>>[Vue warn]: Unknown custom element: <my-component> - did you register the component correctly? For recursive components, make sure to provide the "name" option.

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



## `<component>`

## `<slot>`

## `<transition>`

## `<keep-alive>`
