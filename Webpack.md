
- Webpack是当下最流行前端构建工具
- 核心概念
  - entry 入口文件，一个模块的入口，可以配置成数组
  - loader 文件转换器，把不常用的文件类型转换成可加载的数据
  - plugin 扩展webpack功能的插件。通过在生命周期节点上加入扩展hook，添加功能。
  - chunk 多个文件组成一个代码块，打包 输出

- webpack构建流程
    1. 初始化配置 合并命令参数和配置文件参数
    2. 开始编译
    - 初始化Compiler对象
    - 注册配置的插件
    - 执行Compiler对象的run方法开始编译
    3. 确定入口
       荣entry入口开始解析文件构建AST，找出依赖，递归查找构建
    4. 编译模块 在递归构建AST语法树的时候，使用Loader对文件进行转换处理
    5. 根据依赖管理和打包配置生成不同的chunk
    6. 输出chunk到文件系统

- 在构建的生命周期内有一系列的hook可以执行挂载的插件，扩展webpack的功能


Webpack的优化
---------------------------
+ Webpack的优化
    * ree sharking
    * external
    * 优化开发体验
    + 优化构建速度
        * 在配置loader时通过include缩小命中范围
        * babel开启cacheDirectory
        * 优化resolve.modules 为第三方模块的绝对路径
        * 优化resolve.mianFields配合
        * 优化resolve.alias配置
        * 优化resolve.extensions
        * 后缀尝试列表尽可能的小
        * 频率出现最高的文件后缀优先放在最前面
        * 在源码写导入语句时，尽可能的带上后缀，避免寻找过程
        * 优化module.noParse配置
        * 使用HappyPack插件
        * 使用多进程，发挥多核CPU的能力
        * 使用 ParallelUglifyPlugin
        * 多进程压缩代码
    + 优化使用体验
        * 使用自动刷新
        * 开启模块的热替换
    + 减少首屏加载时间
        * 区分环境
- NODE_ENV
- 压缩代码
 - uglifyJS
 - cssnano

 - CDN加速

 - 修改publicPath配置

  - 使用Tree shaking
  - 提取公共代码
  - 按需加载

    - 使用动态import
+ 提升流畅度
    * 使用Prepack
    * 在编译阶段对可以求值的部分进行求值
    * 开启Scope Hoisting
    * 自动合并可以合并的模块


# 学习资源
  - 深入浅出Webpack- http://webpack.wuhaolin.cn/