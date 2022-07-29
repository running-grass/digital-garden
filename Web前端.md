Cookie的有效期
---------------------------

Cookie的有效期
   :PROPERTIES:
   :CUSTOM_ID: cookie的有效期
   :END:
设置Cookie的生存期。有两种存储类型的Cookie：会话性与持久性。Expires属性缺省时，为会话性Cookie，仅保存在客户端内存中，并在用户关闭浏览器时失效。

持久性Cookie会保存在用户的硬盘中，直至生存期到或用户直接在网页中单击"注销"等按钮结束会话时才会失效
。


CORS
---------------------------

CORS
   :PROPERTIES:
   :CUSTOM_ID: cors
   :END:
CORS是一个[[W3C]]标准，全程是"跨域资源共享"(Cross-origin resource
sharing) *
Access-Control-Allow-Origin：可接受的域，是一个具体域名或者*，代表任意

它允许浏览器向跨源服务器发出[[XMLHttpRequest]]请求，从而克服了AJAX只能同源使用的限制 
#同源策略 + 如果是te'shu'qing的话 *
会在正式通信之前，增加一次[[HTTP]]查询请求，称之为”预检“请求(preflight)

浏览器先询问服务器，当前网页所在的域名是否在服务器的许可名单之内，以及可以使用那些HTTP动词和头信息字段，再行判断当前的域名、请求类型和头信息是否都在许可范围之内
+ 当浏览器收到答复后， * 如果是的话，则正是发出[[XMLHttpRequest]]请求 *
否则报错

Access-Control-Allow-Credentials：是否允许携带cookie，默认情况下，cors不会携带cookie，除非这个值是true
+ 浏览器会把[[Ajax]]请求分为两类 + 简单请求 *
HEAD、GET、POSTsan'zhong'qing'qi + 头信息不超过以下几个字段 * Accept *
Accept-Language * Content-Language * Last-Event-ID * ((uce-Content-Type))（

te'shu'qing + 原理 +
当浏览器发现[[Ajax]]请求是简单请求时，会在请求头携带一个字段=Origin= *
=Origin: http://grass.work:80= + 服务端会根据这个值是否允许其跨域 *
如果服务器允许跨域，

Content-Type：只限于三个值application/x-www-form-urlencoded、multipart/form-data、text/plain
+ 如果想在跨域请求中操作[[Cookie]]，需要同时满足3个条件 *
服务器的响应头中=Access-Control-Allow-Origin=true= *
浏览器发起[[Ajax]]时需要制定=withCredentials=true= *
响应头中的=Access-Control-Allow-Origin=不能为=*=，一定要为制定的域名


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


前端工程化
---------------------------

前端工程化
   :PROPERTIES:
   :CUSTOM_ID: 前端工程化
   :END:

- 随着项目规模的扩大，需求越来越复杂，开发人员的增多，对质量的要求更高，会引发一些问题

  - 重复的琐碎工作 需要自动化

    - 构建
    - 部署
    - 测试
    - 集成

  - 沟通成本上升 需要规范化
  - 代码冲突和重复代码 需要模块化和组件化

- [[模块化]]  文件的层面上

  - [[js模块化]]

    - 加载和打包 webpack，rollback

  - [[css模块化]]

    - scss，less等产品
    - css规范 避免污染全局css空间

      - [[BEM规范]]

  - 资源模块化

    - webpack

- [[组件化]] 在一个完整的开箱即用的组件的复用
- [[规范化]]

  - 目录结构的制定
  - 编码规范

    - eslint

  - 前后端接口规范

    - restful

  - 文档规范

    - jsdoc

  - 组件管理
  - Git分支管理

    - gitflow

  - Commit描述规范

    - commitizen

  - 定期CodeReview
  - 视觉图标规范

- [[自动化]]

  - 图标合并 使用webpack
  - 自动化集成
  - 自动化构建
  - 自动化部署
  - 自动化测试

    - jest


前端测试
---------------------------
+ 大致分为三种
    * 单元测试——主要是纯代码，或者公共的纯组件
    * 集成测试——执行端到端的测试，模拟用户操作
    * 自动化UI测试——自动对快照进行比较
+ 测试需要考虑的问题
    * 测试问题的可复现性
    * 和sonar质量管理工具的集成
    * 和开发流程的集成，不阻碍开发流程，并且可以帮助更好的程序设计与开发





HTTP状态码
---------------------------

HTTP状态码
   :PROPERTIES:
   :CUSTOM_ID: http状态码
   :END:

- 1xx 信息

  - 100 继续，客户端继续其请求
  - 101 切换协议

- 2xx 成功

  - 200 OK，请求成功
  - 201 已创建
  - 202 已接受，但未处理完成
  - 203
  - 204 无内容

- 3xx 重定向

  - 300 多种选择资源位置
  - 301 永久移动
  - 302 临时移动
  - 303
  - 304 文件未修改
  - 305 必须使用代理

- 4xx 客户端错误

  - 400 请求的语法错误
  - 401 请求用户需要身份认证
  - 403 服务端理解客户端的请求，但是拒绝执行此请求
  - 404 文件未找到

- 5xx 服务器错误

  - 500 服务器内部错误
  - 502 网关收到了远程服务器的无效响应
  - 503 由于超载或者系统维护，服务器暂时无法处理请求
  - 504 网关超时

- [[HTTP]]



HTTP请求头信息
---------------------------

HTTP请求头信息
   :PROPERTIES:
   :CUSTOM_ID: http请求头信息
   :END:
Content-Type：只限于三个值application/x-www-form-urlencoded、multipart/form-data、text/plain

Access-Control-Request-Method：接下来会用到的请求方式，比如PUT *
Access-Control-Request-Headers：会额外用到的头信息



HTTP响应头信息
---------------------------

HTTP响应头信息
   :PROPERTIES:
   :CUSTOM_ID: http响应头信息
   :END:

- Access-Control-Allow-Origin：可接受的域，是一个具体域名或者*，代表任意

Access-Control-Allow-Credentials：是否允许携带cookie，默认情况下，cors不会携带cookie，除非这个值是true

Access-Control-Allow-Methods：允许访问的方式 *
Access-Control-Allow-Headers：允许携带的头

Access-Control-Max-Age：本次许可的有效时长，单位是秒，过期之前的ajax请求就无需再次进行预检了




IndexedDB
---------------------------

IndexedDB
   :PROPERTIES:
   :CUSTOM_ID: indexeddb
   :END:

- 特点

  - 键值对存储
  - 同源策略
  - 异步操作
  - 支持事务
  - 存储空间大
  - 支持二进制

- 基本概念

  - 数据库：IDBDatabase 对象

    - 每个域名（严格的说，是协议 + 域名 + 端口）都可以新建任意多个数据库
    - 版本的概念

      - 同一个时刻，只能有一个版本的数据库存在
      - 如果要修改数据库结构（新增或删除表、索引或者主键），只能通过升级数据库版本完成。

  - 对象仓库：IDBObjectStore 对象

    - 每个数据库可以新建若干的对象仓库
    - 类似于关系数据库中的表的概念

  - 数据记录

    - 对象仓库保存的是数据记录
    - 每条记录类似于关系型数据库的行
    - 只有主键和数据体两部分。

      - 主键可以是数据记录里面的一个属性
      - 也可以指定为一个递增的整数编号

  - 索引： IDBIndex 对象
  - 事务： IDBTransaction 对象

    - 数据记录的读写和删改，都要通过事务完成。

  - 操作请求：IDBRequest 对象
  - 指针： IDBCursor 对象
  - 主键集合：IDBKeyRange 对象




TCP
---------------------------

TCP
   :PROPERTIES:
   :CUSTOM_ID: tcp
   :END:

- [[网络协议]]
- 传输控制协议 (Transmission Control Protocol)
- 特点

  - 传输层
  - 面向连接
  - 可靠





TCP传输中的三次握手和四次挥手策略
---------------------------

TCP传输中的三次握手和四次挥手策略
   :PROPERTIES:
   :CUSTOM_ID: tcp传输中的三次握手和四次挥手策略
   :END:

- 目的是为了吧数据准确无误的送达mu'biao'ch
- 具体流程

  - 三次握手

    - 发送端发送一个带SYN标志的数据包给接收方
    - 接收方收到后，回传一个带有SYN/ACK标志的数据包以示传达确认信息
    - 发送端再回传一个带ACK标志的数据包，代表握手结束

  - 一个[[TCP]]连接建立完成，如果握手途中某个阶段莫名中断，[[TCP]]协议会再次以相同的顺序发送相同的数据包
  - 断开一个TCP需要四次握手

    - 主动关闭方发送一个FIN，用来关闭主东方到被动方的数据传送

      - 告诉被动方，我不给你新数据了
      - 如果FIN信号之前的数据没有收到确认，还是会重发的
      - 主动方在FIN信号之后还是会接收数据

    - 被动方收到FIN后，发送一个ACK给对方，确认序号为收到序号+1

      - 需要SYN相同，一个SYN占用一个序号

    - 被动方发送一个FIN，关闭到主动方的新数据传送。

      - 但是还是能接收数据，比如主动方FIN之前迟到的数据

    - 主动方收到FIN后，发送一个ACk给被动方，确认序号为收到序号+1

  - 支持完成四次握手，结束了一次[[TCP]]对话



TCP和UDP的区别
---------------------------

TCP和UDP的区别
   :PROPERTIES:
   :CUSTOM_ID: tcp和udp的区别
   :END:

- [[TCP]]面向连接，而[[UDP]]无连接
- [[TCP]]可靠性高，[[UDP]]可靠性低
- [[TCP]]传输速度略慢，[[UDP ]]



UDP
---------------------------

UDP
   :PROPERTIES:
   :CUSTOM_ID: udp
   :END:

- [[网络协议]]
- 用户数据报协议 (User Datagram Protocol)
- 特点

  - 传输层
  - 无连接
  - 不可靠
  - 快速传输




JAMStack
---------------------------

JAMStack（JAM 代表 JavaScript，API 和 Markup）是一种使用[[SSG]] 技术、不依赖 Web Server 的前端架构。 它的核心是：不依赖 Web Server。 +
+ 优点
    * 高性能：由于网页是静态生成的，没有额外的网络数据请求，它的([[TTFB]])性能是最佳的（因为不涉及后端、数据库等等）。
    * 易部署：因为 JAMStack 不依赖 Web Server，部署就仅仅是把生成的网页放到[[CDN]] 就可以了。
    * 强安全：同样因为不依赖 Web Server 的原因，就导致JAMStack 网站的攻击面很小。
    * 易开发：JAMStack，由于其特性，开发也极其简单，不强依赖后端，开发、测试仅仅是部署到一个静态文件服务器即可。现在「三大框架」都有相应的SSG 方案，学习成本不高。
    + 三大前端框架对应的SSG方案
        * Next.js 是基于React 的 [[SSR]]/[[SSG]] 框架。
        * Scully 是基于 Angular 的 [[SSG]]框架。
        * VitePress 是 [[Vue]] 官方推出的 [[SSG]] 框架。




- 步骤

  - 申请小程序
  - 开发代码
  - 发布小程序

- tips

  - mpvue是支持小程序原生组件的
  - mpvue不支持直接在template上直接绑定函数

- 生命周期
- 小程序框架


  - mpVue
  - Uni-App
  - Taro
  - WePy
  - Chamelon
  
- 小程序组件库

  - vant weapp
  - weui
  - iview weapp
  - colorui
  - Wux weapp
  - taroUi
  - linUI
  - MinUI






跨域问题
---------------------------

跨域问题
   :PROPERTIES:
   :CUSTOM_ID: 跨域问题
   :END:
[[跨域]]问题的存在是由于[[浏览器]]对于[[AJAX]]请求的一种安全限制，一个页面发起的[[Ajax]]请求，只能是于当前页同域名的路径，这能有效的阻止[[跨站攻击]]
* 但是在实际开发中，经常会出现多台服务器之间的交互，多个内部服务的交叉调用，地址和端口都可能不同



跨域
---------------------------

跨域
   :PROPERTIES:
   :CUSTOM_ID: 跨域
   :END:

- 跨域是指跨[[域名]]的访问
- 跨域的qing'k

  - [[域名]]不同
  - 二级[[域名]]不同
  - [[域名]]相同但是[[端口]]不同
  - [[域名]]和[[域名]]对应的[[IP]]
  - 同[[域名]]但是不同[[协议]]




同源策略
---------------------------

同源策略
   :PROPERTIES:
   :CUSTOM_ID: 同源策略
   :END:

- 由[[Netscape]]提出的一个著名的[[安全策略]]

加载一个脚本是会判断该脚本和当前页面是否是同一个域名，只有同一个域名的脚本才会被执行，如果不同域名，浏览器会报一个异常，提示拒绝fang'wen
* 同源策略只是一个单纯的浏览器端的行为，如果使用非浏览器的方式请求非同源脚本不会触发[[跨域问题]]
* 只有[[协议]]、[[域名]]、[[端口]]全部相同时才会被认为是同源


如何解决跨域问题
---------------------------

如何解决跨域问题
   :PROPERTIES:
   :CUSTOM_ID: 如何解决跨域问题
   :END:

- [[跨域问题]]
- [[JSONP]] #解决方案

  - 原理

    - =script=标签可以进行跨域请求js文件，通过执行url中的回调函数实现跨域

  - 实现

    - jian'dan'shi'xian

      - 在html页面中定义一个函数，例如=showJson=
      - 在目标js文件中写入=showJson({a:1})=
      - 使用js动态插入=script=标签，在url后面加入callba

        - 使用js动态插入=script=标签，在url后面加入callback参数

      - 使用js动态插入=script=标签，在url后面加入callback参数

        - 使用js动态插入=script=标签，在url后面加入callback参数，前提

      - 优点

        - 简单易用
        - 无依赖类库

      - 缺点

        - 只能使用GETqin

    - [[JQuery]]实现

      - =$.ajax=方式

        - dataType设置成jsonp
        - jsonp为url中的参数名，默认为callback，可以手动指定
        - jsonpCallback为请求返回后的回调函数名称，如果不指定默认使用success回调使

          - 在url中增加=jsoncallback=?=，直接在回调函数中接收json返回值

      - =$.getJSON=方法
      - 优点

        - 可以有GET和POST的选择

      - 缺点

        - 返回的文件格式依旧为JSONP

  - 优点

    - 兼容性好

  - 缺点

    - 只能支持=GET=请求

- [[CORS]]#解决方案

  - #解决方案

    - 原理

      - 所有的浏览器都支持=Headers=中的=Cross-origin=系列

    - 实现

      - 在服务器端返回中增加=Access-Control-Allow-Origin=头信息，值设置为需要允许的域名，可以使用通配符

    - 优点

      - 前端不需要额外配置和关心
      - 服务端统一拦截处理
      - 可以自定义跨域规则
      - 支持各种qing'qiu

    - 缺点

      - 使用复杂请求是会增加一次=OPTIONS=请求

- [[Nginx]]反向代理 #解决方案

  - 原理

    - 利用[[Nginx]]的反向代理功能，统一域名

  - 实现

    - 把多个域名映射为同一域名下的多个路径空间

  - 优点

    - 集中式管理跨域
    - 增加服务时，可以只用配置一次

  - 缺点

    - 需要在[[Nginx]]进行额外的配置，多引入一个模块
    - 语义不清晰
    - 对于精细化的[[跨域]]控制无能为力

- [[IFrame]]+=[[document.domain]]= (仅适用同主域名) #解决方案

  - 原理

    - [[document.domain]]可以把值设置为当前域的父域

  - 实现

    - 在a.html页面中使用js动态创建并加载页面b.html
    - 在b.html修改[[document.domain]]为和a.html页面相同的父域名
    - 把a.html也设置一下[[document.domain]]

  - 优点

    - 不借助第三方类库

  - 缺点

    - 只适用于同一个主域名的跨域情况
    - 前端和后端都需要特殊处理

- [[IFrame]]+[[postMessage]]



SSG
---------------------------

SSG
   :PROPERTIES:
   :CUSTOM_ID: ssg
   :END:

- Static Site Generators
- 博客生成程序

  - Jekyllrb https://jekyllrb.com/
  - Hexo https://hexo.io/
  - Octopress http://octopress.org/

[[https://www.cnblogs.com/buyz/p/10935831.html][11个最流行的静态(博客)网站生成工具]]





# Cookie 安全相关的设置
## HttpOnly
