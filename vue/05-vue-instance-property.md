# Vue Instance Property

## vm.$options
Vue实例的初始化选项

## vm.$el
vue实例监控的根DOM元素

## vm.$data
- Vue监控的data对象。
- 实际Vue实例代理了对data对象属性的访问
## vm.$root
- Vue组件的根实例
- 如果没有父实例，此实例指代自己

## vm.$slot
- 访问被插槽分发的内容：`vm.$slot.foo`

## vm.$parent
- 访问父实例/组件

## vm.$refs
- 访问子组件实例
- `vm.$refs.usernameInput`
