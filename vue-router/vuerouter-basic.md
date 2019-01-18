# Vue Router 
- Vue Router简介
- VueRouter()是一个构造函数
- 创建Vue Router的步骤

## Vue Router简介
- 有了路由器，可以管理家里的每台电脑
- 有了Vue Router，可以管理项目中的每个组件

## VueRouter()是一个构造函数
`VueRouter()`构造函数用于创建一个router实例。

![VueRouter构造函数](images/vuerouter-constructor.png)
```
function VueRouter (options) {
    if ( options === void 0 ) options = {};

    this.app = null;
    this.apps = [];
    this.options = options;
    this.beforeHooks = [];
    this.resolveHooks = [];
    this.afterHooks = [];
    this.matcher = createMatcher(options.routes || [], this);

    var mode = options.mode || 'hash';
    this.fallback = mode === 'history' && !supportsPushState && options.fallback !== false;
    if (this.fallback) {
        mode = 'hash';
    }
    if (!inBrowser) {
        mode = 'abstract';
    }
    this.mode = mode;

    switch (mode) {
        case 'history':
            this.history = new HTML5History(this, options.base);
            break
        case 'hash':
            this.history = new HashHistory(this, options.base, this.fallback);
            break
        case 'abstract':
            this.history = new AbstractHistory(this, options.base);
            break
        default:
            {
            assert(false, ("invalid mode: " + mode));
            }
    }
}
```

## 创建Vue Router的步骤
**第一步：引入vue-router库**
```
import VueRouter from 'vue-router'
```

**第二步：安装路由插件**
```
Vue.use(VueRouter)
```

**第三步：创建Router实例**
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

## Router对象

**打印this.$router**
![this.$router](images/this-router-object.png)

**Router对象简介**

- `Router`对象是VueRouter()的实例对象。
- 



**访问Router对象的方法**

当向`Vue`实例注入`Router`实例之后，可以在任何组件内通过 `this.$router` 访问路由器

**Router对象的属性**

**Router对象的方法**


## Route对象

**打印this.$route**

![this.$route](images/this-route-object.png)

**访问Route对象的方法**

当向`Vue`实例注入`Router`实例之后，可以在任何组件内通过 `this.$route` 访问当前路由的信息


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
