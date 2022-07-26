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
