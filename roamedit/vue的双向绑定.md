vue的双向绑定
---------------------------
* [[前端]]，[[面试题]]，[[Vue]]
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
