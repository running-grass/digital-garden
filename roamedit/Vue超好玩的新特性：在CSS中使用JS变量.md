Vue超好玩的新特性：在CSS中使用JS变量
---------------------------
* #+tags: 前端，Vue，CSS

Vue超好玩的新特性：在CSS中使用JS变量
:PROPERTIES:
:id: vue超好玩的新特性在css中使用js变量
   :CUSTOM_ID: vue超好玩的新特性在css中使用js变量
:END:

- 使用到[[CSS函数]]中的var函数

  - 例子

    - ```css

  - var(custom-property-name, value)

    - custom-property-name 必需。自定义属性的名称，必需以 -- 开头。
    - value 可选。备用值，在属性不存在的时候使用。

  - 用于插入自定义的属性值。

- uce-s6CiALQ))}}
- 在[[Vue3]]中使用css中的var且支持数据驱动

  - ```html

- 原理

  - 类似通过控制=dom.style.setPropterty('--width', this.widthVar)=

- 不兼容IE
