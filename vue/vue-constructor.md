# Vue Constructor

## 关于Vue Constructor的理解
- 首先，我们把App看做一个对象。
- `Vue()`将App对象创建变为标准化流程。


## Print Vue Constructor
![Vue Constructor](./images/vue-constructor.png)


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

## Vue.component('component-name',{options})
- 用途：注册组件(global)

## Vue.use(plugin)

## Vue.extend()
使用基础 Vue 构造器，创建一个“子类”。参数是一个包含组件选项的对象。

## Vue.filter()
