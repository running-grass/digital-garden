Hexo的介绍及安装使用
---------------------------

Hexo的介绍及安装使用
:PROPERTIES:
:id: hexo的介绍及安装使用
   :CUSTOM_ID: hexo的介绍及安装使用
:END:

- 什么是Hexo

  - Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用
    Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页

- Hexo的特点

  - 基于Node.js
  - 极速sheng'che
  - 支持Markdown
  - yi'jian'bu'shu
  - 插件丰富

- an'zhuang

  - 安装Hexo命令行工具

    - npm install hexo-cli -g

  - 初始化项目

    - hexo init blog

  - 安装依赖

    - cd blog
    - npm install

  - 启动shi'shi'yu'lan

    - cd blog
    - hexo server
    - 此时可以到localhost:4000/ 查看效果

- 更换z

  - 安装主题NexT

    - cd blog
    - git clone https://github.com/next-theme/hexo-theme-next
      themes/next

  - 修改配置

    - 打开blog/_config.yml文件
    - 找到theme: landscape
    - 修改为theme: next
    - 重启server生效

- 编辑博文

  - 新建一篇博文

    - hexo new "hello-hexo"

  - 编辑内容

    - 打开blog/source/_posts/hello-hexo.md
    - 在第二个---下面写入文章nei
    - 刷新网页，查看更新后的xiao'guo

- 完善配置

  - title: 奔跑的小草
  - subtitle: 一只野生程序猿，爱越野，爱滑雪
  - description: 分享一些技术上的文章
  - keywords: IPFS,Hexo,Vue
  - author: 刘世华
  - language: zh-CN
  - timezone: Asia/Shanghai
