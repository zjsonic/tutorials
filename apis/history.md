# History Interface


## 打印history对象

![History Object](images/history-object.png)

## 用途
`histroy`接口允许操作浏览器中的session记录。
- session记录由history对象创建
- session记录记录了当前窗口或当前tab内访问过的页面
- history对象表示`session history entries`的一个列表。
- 每一个`session history entry`都包含：
  - url
  - state obj
  - title
  - document obj
  - form data
  - 滚动位置

## History和history
- `History`是一个构造函数，用来定义具有共同属性和方法的一组对象。
- `history`是一个实例化的`History`，由`new History()`而来。用来访问特定的`history`对象信息。

## window.history
`window`对象的history属性返回的`history`对象必须与当前window对象的`document`对象保持一致。

## 属性
- history.length

## 方法
- history.back():Goes to the previous page in session history
- history.forward():Goes to the next page in session history
- history.go(): Loads a page from the session history, identified by its relative location to the current page
- history.pushState():Pushes the given data onto the session history, with the given title, and, if provided, the given URL.
- history.replaceState() : Updates the current entry in the session history to have the given data, title, and, if provided, URL.
