处理群晖NAS中的烦人eaDir文件夹
---------------------------

处理群晖NAS中的烦人eaDir文件夹
   :PROPERTIES:
   :CUSTOM_ID: 处理群晖nas中的烦人eadir文件夹
   :END:

- 

  1. 删除所有@eaDir文件夹

  - 切换到root账号

    - sudo -i

  - 看看你有多少个卷空间，默认*号基本是1开始

    - ls -d /volume*

  - 删除所有卷下所有@eaDir文件夹

    - find /volume* -name "@eaDir" -type d -print0 | xargs -0 rm -rf

- 

  2. 停止生成@eaDir文件夹

  - @eaDir文件夹是因为群晖DSM系统"全局搜索"服务产生的。如果平时用不上群晖的"全局搜索"服务，可以直接关闭。如果你使用DS
    Drive、Video Station、Moments，不建议关闭！
  - 关闭方法：仍然是root账号下执行以下命令
  - =synoservice --disable pkgctl-SynoFinder=
