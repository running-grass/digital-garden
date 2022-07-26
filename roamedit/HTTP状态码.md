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
