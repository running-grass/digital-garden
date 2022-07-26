DOM的回流和重绘
---------------------------

DOM的回流和重绘
   :PROPERTIES:
   :CUSTOM_ID: dom的回流和重绘
   :END:

- 页面呈现过程

  - 根据html解析dom tree
  - 根据css解析样式结构体
  - 结合dom tree和样式结构体构建render tree
  - 根据render tree渲染页面

当元素的位置、尺寸、布局、显示隐藏、窗口大小发生变化的时候，会引发回流，即重构dom
tree或render tree * 当样式发生改变的话，会直接更新render tree，引发重绘

回流一定引发重绘，重绘不一定引发回流 *
通过构建文档片段，修改文档碎片的属性。统一插入到dom中，只会触发一次回流和重绘，否则会很多次
* vdom可以减少回流和重绘的次数
