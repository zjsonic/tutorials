# Transition

## 用途
- `transition`属性允许你控制css属性值变化的过程。
- 通常，css属性值的变化是瞬间完成的：
  - 只能看到属性值的变化结果
  - 看不到变化的过程

## Usages of Transition
- initial state
  - set initial value of the property you wanna control
  - apply `transition` property
- changed state
  - set target value of the property you wanna control

## Properties
|Property|value|Description|
|-|-|-|
|transition-property||Specifies the property you wanna control.|
||property|a comma separated list|
||all|Default value. All properties will get a transition effect|
||none|None property will get a transition effect|
|transition-duration||Specifies how many seconds or milliseconds the transition effect takes to complete|
||seconds||
||milliseconds||
|transition-delay||Specifies a delay for a transition effects|
||seconds||
||milliseconds||
|transition-timing-function||Specifies the speed curve|
||ease||
||ease-in||
||ease-out||
||ease-in-out||
||linear||
|transition|p d d f|a shorthand property|
