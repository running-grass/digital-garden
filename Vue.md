前端框架， 新版的vue3已经支持 [[TypeScript]]

vue的双向绑定
---------------------------
* [[Web前端]]，[[面试题]]，[[Vue]]
+ 面试回答
:PROPERTIES:
:id: vue的双向绑定
:END:
    * 使用onChange监听input的变化，更新data的值
    * 使用数据劫持+发布订阅的方式来触发对view的更新

-
+ 主要分三步
    * 使用model层的数据编译view层
    * model的更新会触发view的更新
+ 简述
    * 劫持数据，通过设置访问器属性来监听数据的变化，从而触发DOM更新
+ 具体实现
    * 在Vue实例初始化的时候，为data中的每个数据使用Observe封装，也就是增加访问器属性get和set
    * 在编译view的时候，为每个绑定了数据的dom创建一个Watcher，提供一个update方法用来更新dom
    * 为每个Observe创建一个Dep，把一个Observe和多个Watcher关联到一起
    * 当Observe监听到数据改变后，触发Dep的notify，从而通知关联的多个Watcher更新Dom
    * view中数据的变化会更新model
    * 监听输入框的onChange事件，把输入框的value赋值给绑定的model数据
    * computer中的数据如果想要更新，需要设置成访问器属性




Vue组件通信方式
---------------------------

Vue组件通信方式
   :PROPERTIES:
   :CUSTOM_ID: vue组件通信方式
   :END:

- vuex
- 事件总线
- props/emit 父子
- =$parent/$children= 父子
- =ref/$refs= 父子
- =props/$emit= 父子
- =$attrs /$listeners= 父子 跨级
- =provide / inject= 父子 跨级
- =localstroage/sessionstroage= 跨级 兄弟 父子





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




如何理解虚拟dom
---------------------------

如何理解虚拟dom
   :PROPERTIES:
   :CUSTOM_ID: 如何理解虚拟dom
   :END:

- 是真实的DOM的数据抽取出来，以对象的形式模拟树形结构
- 特点

  - 对真实dom的抽象，赋予了框架的跨平台性，可以在浏览器使用，也可以在安卓、IOS和小程序等端使用
  - 提供了diff算法，减少了操作真实dom的性能消耗

- diff

  - 用JS模拟真实DOM节点把虚拟DOM转换成真实DOM插入页面中发生变化时，比较两棵树的差异，生成差异对象根据差异对象更新真实DOM
