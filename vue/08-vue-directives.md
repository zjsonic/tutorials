# Directives

## 1.更新内容：2
- v-text: 更新元素的 `textContent`
- v-html: 更新元素的`innerHTML`

## 2.绑定数据：2
- v-bind
  - 绑定一个参数
    - `<img v-bind:src="imageSrc">`
    - `<img :src="'/path/to/images/' + fileName">`
    - `<div v-bind:text-content.prop="text"></div>`
    - `<my-component :prop="someThing"></my-component>`
    - `<child-component v-bind="$props"></child-component>`
  - 绑定一个对象
    - `<div :class="{ red: isRed }"></div>`
    - `<div :class="[classA, classB]"></div>`
    - `<div :style="{ fontSize: 20 + 'px' }"></div>`
    - `<div v-bind="{ id: someProp, 'other-attr': otherProp }"></div>`
  - 修饰符
    - .prop
    - .camel
    - .sync
- v-model: 在表单空间或组件上创建双向绑定
  - 应用对象
    - `<input>`
    - `<select>`
    - `<textarea>`
    - `component`
  - 修饰符
    - .lazy
    - .number
    - .trim

## 3.处理事件：1
- v-on: 绑定事件监听器
  - 属性值
    - 函数
    - 表达式
    - 对象
  - 修饰符
    - `.native`
    - `.prevent`

## 4.渲染元素：6
- v-once: 一次性渲染元素和组件 no-value
- v-show: 切换元素的display属性（css属性）
- v-for: 循环渲染元素
- v-if: 条件渲染元素
- v-else-if: 条件渲染元素
- v-else: 条件渲染元素

## 5.加快编译：2
- v-cloak: 隐藏未编译的mustache no-value
- v-pre: 跳过没有指令的节点，加快编译。no-value
