# Vue教程
- Vue Installation
- Vue Constructor
- Vue Instance


## Vue Installation

**方法一：直接下载引入**

```
<script src = './js/vue.js'></script>
```
- `Vue`会被注册为一个全局变量。

**方法二：使用CDN引入**

```
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.17/dist/vue.js"></script>
```

**方法三：在webpack下使用NPM引入**

```
$ npm install vue
```

**方法四：使用VUE-CLI引入**

```
$ npm install -g @vue/cli
$ vue create projectName
```

检测是否安装成功
```
$ vue --version
```

## Vue Constructor
**Vue($Options)是一个构造函数**

>构造函数：在JS中，如果一个函数用来初始化一个新建对象，那么这么函数就是构造函数。

我们把APP看做一个对象
- Vue()实现了创建App对象流程的标准化
- $options是一个对象：使用选项创建你想要的行为。

```
const vm = new Vue({
  //DOM类： 用于创建DOM结构
    el:
    template:
    render:
    renderError:
  //数据类：用于向DOM中注入数据(数据可以是响应的)
    data:
    props:
    propsData:
    methods:
    computed:
    watch:
  //生命周期钩子：在实例对象被创建的整个过程中(前、中、后)可以执行我们自己代码的函数。
    beforeCreate:
    created:
    beforeMount:
    mounted:
    beforeUpdate:
    updated:
    actived:
    deactived:
    beforeDestroy:
    destroyed:
    errorCaptured:
  //资源
    components:
    directives:
    filters:
  //组合
    parent:
    mixins:
    extends:
    provide:
  //其他
    name:
    model:
    delimiters:
    functional:
    inheritAttrs:
    comments:
})
```

**Vue()的属性**

主要用来对Vue进行全局配置；
- Vue.config: 是一个对象。对Vue构造函数进行全局配置(如：日志与警告、是否开启开发工具等)
- Vue.version: 获取Vue的版本号，对插件开发者非常有用。

**Vue()的方法**

主要用来扩展Vue的功能；
- Vue.extend(): 基础Vue构造器，用于创建“子类”。(组件就是子类)
- Vue.use(): 安装Vue.js插件。
- Vue.component(): 注册全局组件、获取全局组件。
- Vue.filter(): 注册全局过滤器、获取全局过滤器。
- Vue.directive(): 注册全局指令、获取全局指令。
- Vue.mixin(): 注册全局混入。
- Vue.compile(): 在render()函数中编译模板字符串。
- Vue.nextTick():
- Vue.observable(): 让一个对象可响应。
- Vue.set(): 向响应式对象上添加新属性。
- Vue.delete(): 删除对象的属性。

## Vue Instance
**Vue实例是由Vue构造函数创建的对象**

- 每个应用都是从创建一个VUE实例开始的。
- 当创建Vue实例的时候，可以传入一个选项对象，来描述你希望的行为(要管理的DOM和数据)。
- 一个Vue应用由一个Vue根实例以及组件树构成。


**创建实例对象的语法**

```
const vm = new Vue($Options)
```
**vm的属性**
- 第一组
  - vm.$data
  - vm.$props
  - vm.$isServer
  - vm.$route: 返回当前路由对象。(若未添加VueRouter，则返回undefined) 包含以下信息
    - $route.fullPath:返回解析后的URL(包含路径+查询字符串+hash字符串)
    - $route.path:返回当前路由的路径部分(端口号后面，查询字符串前面)
    - $route.query:
    - $route.hash:
    - $route.params:
    - $route.matched:
    - $route.name
  - vm.$router: 返回路由对象。
  - vm.$ssrContext
  - vm.get $attrs
  - vm.set $attrs
  - vm.get $listeners
  - vm.set $listeners
- 第二组
  - vm.$attrs
  - vm.$children
  - vm.$createElement
  - vm.$el
  - vm.$listeners
  - vm.$options
  - vm.$parent
  - vm.$refs
  - vm.$root
  - vm.$scopedSlots
  - vm.$slots
  - vm.$vnode
- 第三组
  - `_c`
  - `_data`
  - `_directInactive`
  - `_events`
  - `_hasHookEvent`
  - `_inactive`
  - `_isBeingDestroyed`
  - `_isDestroyed`
  - `_isMounted`
  - `_isVue`
  - `_renderProxy`
  - `_routerRoot`
  - `_self`
  - `_staticTrees`
  - `_uid`
  - `_vnode`
  - `_watcher`
  - `_watchers`

**vm的方法**
- `vm.__proto__.$watch`
- `vm.__proto__.$set`
- `vm.__proto__.$delete`
- `vm.__proto__.$on`
- `vm.__proto__.$once`
- `vm.__proto__.$off`
- `vm.__proto__.$emit`
- `vm.__proto__.$mount`
- `vm.__proto__.$forceUpdate`
- `vm.__proto__.$nextTick`
- `vm.__proto__.$destroy`


## 组件
**组件是可复用的Vue实例。**
- 组件可在根实例中作为定义元素使用。
- 组件与实例的区别：
  - 组件的选项对象中没有`el`
  - 组件的选项对象中的`data`是一个函数
  - 组件可以进行任意次数的复用
- 组件名
  - W3C规范：字母全小写且必须包含一个连字符
  - 在DOM中使用时，只有烤串式有效


### 自定义组件
在模板中使用组件时必须先注册Vue才能识别。

**全局注册**

标准语法:

```
Vue.component('id',Vue.extend({ options }))
```
- id: string 指定组件名称
- Vue.extend(): 构造器。创建Vue构造函数的“子类”(子构造函数)。
  - options: 选项对象
    - data: 必须是函数
- Vue.extend()的实例：组件的每一次应用，组件实例会被自动创建

简洁语法:
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


**局部注册**
```
new Vue({
    el: '#app',
    components: {
      'my-component-a': { //OPTIONS },
      'my-component-b': { //OPTIONS }
    }
})
```

**在模块系统中局部注册**

singfile.js or singfile.vue
```
import 'component-a' from './components/component-a'

export default {
  components: {
    `component-a`: component-a
  }
}
```


### 内置组件

**component**:

**slot**

**keep-alive**

**transition**


**transition-group**


## Directives
- v-on
- v-if
- v-else


## Special Attributes
- key
- ref
- is
- slot
- slot-scope
- scope



## Print Vue Constructor
![Vue Constructor](./images/vue-constructor.png)

## Print Vue instance
![Vue instance](./images/vm-without-router2.png)

## Print Vue instance with router
![Vue instance](./images/vm-with-router.png)

## Print Vue Prototype
![Vue Prototype](./images/vue-prototype.png)
