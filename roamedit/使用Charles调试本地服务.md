使用Charles调试本地服务
---------------------------

使用Charles调试本地服务
   :PROPERTIES:
   :CUSTOM_ID: 使用charles调试本地服务
   :END:

- 下载Charles
- 打开Charles
- 打开 proxy =》macOS proxy的开关
- start recording
- 如果是https

  - 在指定的https请求上面右击=》enable ssl proxying
  - 打开help =》 ssh proxying =》 install Charles root catticate

    - 在打开的钥匙串窗口中选择charles proxy 证书
    - 双击打开证书详情

      - 展开信任折叠面板

        - 修改使用此证书是为始终信任
        - 此时下面所有的选项应该都改变为始终信任

- 打开tools =》 rewrite

  - 打开开关

    - 复选enable rewrite选项
    - 复选 debug in error log

  - 编辑重写规则集合

    - 新建一个空的集合

      - 点击add增加一个集合
      - 在右侧顶部修改name

    - 增加域名匹配

      - 单击location框的add按钮，打开编辑框
      - 填写协议、主机、端口、路径等匹配规则，允许通配符

    - 增加重写行为

      - 在rewrite rule框单击add按钮，打开rule编辑框
      - 选择type为url
      - 在match=》value输入框输入 .//client/(./)

        - 勾选输入框后面的regex

      - 在replace =》 value输入框输入 http://localhost:8888/client/$1
      - 点击OK

  - 通过面板开关rewrite
