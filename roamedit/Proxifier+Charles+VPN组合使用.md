Proxifier+Charles+VPN组合使用
---------------------------

Proxifier+Charles+VPN组合使用
   :PROPERTIES:
   :CUSTOM_ID: proxifiercharlesvpn组合使用
   :END:

- 方案背景

  - vpn会修改系统代理，而Charles的使用也是依赖于修改系统代理，所以两个软件会有冲突。当访问一个被墙的域名时，又希望Charles能够劫持请求，或者同时打开被墙域名和需要劫持域名时

- 思路

  - vpn可以长期开着，Charles启动，但是不挂载到系统代理，启动proxifier，全局流量都会走proxifier，然后通过配饰rules进行分流到不同的代理服务，

- 具体步骤

  - vpn打开socket代理，选择pac模式
  - Charles

    - 关闭macos proxy
    - 打开socket代理

  - proxifier

    - 设置proxies

      - 新建两个proxy，分别把vpn和charles的socket代理填上
      - 新建三个proxy chain，分别为

        - 第一个为
        - charles
        - vpn
        - charles->vpn

      - 分别把代理服务器拖入chain中

    - 设置rules

      - 设置default默认规则为直连在最底部
      - 设置vpn为直连，走最前面
      - 中间设置chrome且指定域名，action选择charles
