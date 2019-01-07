# Transition
>If you animate anything else,it's at your own risk,and the chances are you're not going to hit a silky smooth 60 fps. - Paul Lewis & Irish

## 用途
- `transition`属性允许你控制css属性值变化的过程。
- 通常，css属性值的变化是瞬间完成的：
  - 只能看到属性值的变化结果
  - 看不到变化的过程

## Usages of Transition
- apply `transition` property
- trigger transition
  - hover pseudo class
  - class changed
  - js set new Value

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
|transition-timing-function||Specifies the speed curve设置过度曲线（速度曲线）|
||ease||
||ease-in||
||ease-out||
||ease-in-out||
||linear||
|transition|p d f d|a shorthand property|

## properties can be animated
- postion(translate)
- rotation
- scale
- opacity
- font-size
- background-color
- width
- left

## properties can not be animated
- display
- font-family
- position



## References
- [Css Transition from DevTips](https://www.youtube.com/watch?v=8kK-cA99SA0&list=PLqGj3iMvMa4LvJ8VctoXnPI0dtE40wfid&index=1)
