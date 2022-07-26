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
