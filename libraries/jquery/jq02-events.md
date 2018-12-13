
## events
- $(document).ready():当文档完全加载完毕时，执行函数
- $().dblclick(handler) 当鼠标双击元素时触发。为元素绑定双击事件
- $().mouseenter(handler) 当鼠标指针进入元素时触发
- $().mousedown(handler) 当按下鼠标时触发
- $().mouseup(handler) 当释放鼠标时触发
- $().mouseleave(handler) 当鼠标离开元素时触发
- $().hover(mouseenter,mouseleave)
- $().focus(handler) 当表单元素拥有焦点时触发
- $().blur(handler) 当表单元素失去焦点时触发
- $().on('eventName',handler) 为元素绑定一个事件处理函数
- $().on({ event1:handler1(){},event2:handler2(){} }) 为元素绑定多个事件处理函数

## jQuery的方法
- $().hide(speed,callback)
- $().show(speed,callback)
- $().toggle(speed,callback)

- $().fadein(speed,callback) fadein()方法允许fade in一个可见元素
- $().fadeout(speed,callback)  fadeout()方法允许fade out 一个可见元素
- $().fadetoggle(speed,callback) fadetoggle允许在fadein()和fadeout()之间切换
- $().fadeto(speed,opacity,callback)  fadeto()方法允许fade to 指定的opacity


- $().animate({options},speed,callback)
  - {options} : 定义动画中用到的css属性
  - 需要手动为元素设置定位属性:relate fixed absolute
  - If you want to animate color, you need to download the Color Animations plugin from jQuery.com


- $().append()

- $.ajax({options})
```
$.ajax({
  type: 'GET',
  url: '',
  success(result,status,xhr),
  fail(xhr,status,error)
})
```
