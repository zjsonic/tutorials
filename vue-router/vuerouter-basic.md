# Vue Router 
- Vue Router简介
- VueRouter()是一个构造函数
- 创建Vue Router的步骤

## Vue Router简介
- 有了路由器，可以管理家里的每台电脑
- 有了Vue Router，可以管理项目中的每个组件

## VueRouter()是一个构造函数
`VueRouter()`构造函数用于创建一个router实例。

![VueRouter构造函数](images/vue-router.png)


## 创建Vue Router的步骤
**第一步：引入vue-router库**
```
import VueRouter from 'vue-router'
```

**第二步：安装路由插件**
```
Vue.use(VueRouter)
```

**第三步：创建Router实例
```
const router = new VueRouter({
    routes: [
        {
            path: '/',
            component: Home
        }
    ]
})
```
**第四步：将Router实例注入Vue实例中**
```
new Vue({
    router,
    render: h => h(App)
}).$mount('#app')
```

## 组件


- `<router-link>`
    - 用途：在应用中创建导航链接。
    - `to`属性
    - `tag`属性
    - `active-class`
    - `exact-active-class`
    - `exact`
    - `replace`
    - `append`
    - `event`

- `<router-view>`
    - 用途：在应用中渲染组件。(functional组件)
    - `name`
