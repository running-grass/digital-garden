js中阻止事件的方法
---------------------------

js中阻止事件的方法
   :PROPERTIES:
   :CUSTOM_ID: js中阻止事件的方法
   :END:

- preventDefault 阻止事件的浏览器默认行为
- return false  阻止冒泡+默认行为
- stopImmediatePropagation 阻止事件冒泡，且不执行其它事件处理函数
- stopPropagation 阻止事件的冒泡，但是不阻止默认行为
