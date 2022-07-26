stream和transducers的关系
---------------------------

stream和transducers的关系
   :PROPERTIES:
   :CUSTOM_ID: stream和transducers的关系
   :END:

- [[stream]] [[Transducers]]

[[Transducers]]会把用到的函数组合进行复用，而[[stream]]只是在利用小函数进行[[链式调用]]
+ [[Transducers]]和[[Stream]]都可以完成类似的功能和效果 *
对数组只遍历一遍 * [[Stream]]没有办法对一段逻辑过程进行复用。
