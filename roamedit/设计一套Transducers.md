设计一套Transducers
---------------------------

设计一套Transducers
   :PROPERTIES:
   :CUSTOM_ID: 设计一套transducers
   :END:
xf也就是transfomer，把多个变换函数都封装成xf，然后xf们形成了一个链表，xf1.xf
= xf2, xf2.xf = xf3，以此类推直到xfn

在执行reduce时，才会真正生成xf，在执行之前，是尚未链接，但是缓存了当前步骤操作的transducer，

最终，把reducer封装成一个xf，记为xfm,使xfn.xf = xfm

执行的时候，把列表中的某一个数值，先给到xf1，然后xf1处理后，给xf2，最终交给xfm处理，然后开始逐级return。交给最外层reduce函数中的累加器后，开始依次计算下一个数值。

[[https://github.com/cognitect-labs/transducers-js][需要遵循的规范]] *
@@transducer/init * @@transducer/step * @@transducer/result *
@@transducer/reduced * @@transducer/value * @@iterator

[[https://github.com/jlongster/transducers.js][支持的操作]] *
http://cognitect-labs.github.io/transducers-js/classes/transducers.html

map(coll?, f, ctx?) -~~ call f on each item * filter(coll?, f,
ctx?) ~~- only include the items where the result of calling f with the
item is truthy * remove(coll?, f, ctx?) -~~ only include the items where
the result of calling f with the item is falsy * keep(coll?) ~~- remove
all items that are null or undefined * take(coll?, n) -~~ grab only the
first n items * takeWhile(coll?, f, ctx?) ~~- grab only the first items
where the result of calling f with the item is truthy * drop(coll?,
n) -~~ drop the first n items and only include the rest *
dropWhile(coll?, f, ctx?) ~~- drop the first items where the result of
calling f with the item is truthy * dedupe(coll?) -~~ remove consecutive
duplicates (equality compared with ===) * 相关资料

https://jlongster.com/Transducers.js~~A-JavaScript-Library-for-Transformation-of-Data
