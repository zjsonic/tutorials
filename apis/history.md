# History Interface


## 打印history对象

![History Object](images/history-object.png)

## histtory对象简介
- `History`是一个构造函数，用来定义具有共同属性和方法的一组对象。
- `history`是一个实例化的`History`，由`new History()`而来。
- `history`用来创建当前tab内的会话([session](../computer-science/session.md))记录。
- `histroy`接口提供了操作浏览器中的session记录的属性和方法。
- session记录由history对象创建
- session记录记录了当前tab内访问过的页面
- history对象表示`session history entries`的一个列表。
- 每一个`session history entry`都包含：
  - url
  - state obj
  - title
  - document obj
  - form data
  - 滚动位置
  
```
  <script type="text/javascript">
    //History是一个构造函数
    // console.log(History)

    //Window.history表示当前窗口的History对象的引用。
    //History对象：用文档列表形式表示当前窗口的session。注意：1.脚本不能访问已访问过的url，只能访问当前url 2.但可以使用History对象的一些方法访问
    // console.log(history)

    //检测history是否是History的实例
    // console.log(history instanceof History) //true

    //history.length查询当前session的数量
    // console.log(history.length)
    // history.lenght = 10 //只能查询，不能设置
    // console.log(history.length)

    //history.state 返回当前状态对象(1.存储预解析描述)
    // console.log(history.state)

    //history.back() 加载session中的上一个url
    // const btn2 = document.querySelector('#btn2')
    // btn2.onclick = function(){
    //   history.back()
    // }

    //history.forward() 加载session中的下一个url
    // const btn1 = document.querySelector('#btn1')
    // btn1.onclick = function(){
    //   history.forward()
    // }

    //history.go() 按步骤加载session中的url
    // const btn3 = document.querySelector('#btn3')
    // btn3.onclick = function(){
    //   history.go(-2)
    // }

    //history.pushState(stateObj,titleStr,url) 基于当前路径(当前文件夹)创建新的session条目 注意：可以被导航，但不会加载 加载会报404
    //stateObj:可以是被序列化的任何东西  let stateObj = { foo: "bar"}  状态对象改变会触发popstate事件
    //titleStr: 标题
    //url: 新的URL记录



    //history.replaceState()修改当前session条目 场景：响应用户操作(更新状态对象的状态 更新当前session条目)

    //window.onpopstate是popstate事件在window对象上的事件处理程序。
    //popstate:当激活的历史记录条目发生变化时，popstate事件就会在对应的window对象上触发。
    //popstate事件可以通过浏览器行为触发，也可以通过history.back() history.forward() history.go()触发。不可以通过history.pushState()和history.replaceState()触发。

    let boxes = Array.from(document.querySelectorAll('.box'))

    function selectBox (id) {
      boxes.forEach(e => {
        e.classList.toggle('selected', e.id == id)
      })
    }

    boxes.forEach( e => {
      let id = e.id
      e.addEventListener('click', function(){
        history.pushState( {page:`${id}`},`selected: ${id}`,`selected=${id}`)
        selectBox(id)
      })
    })
    window.onpopstate = function(e){
      selectBox(e.state.page)
      console.log("Location" + document.location + ", State:" + JSON.stringify(e.state) )
    }

  </script>
  ```
