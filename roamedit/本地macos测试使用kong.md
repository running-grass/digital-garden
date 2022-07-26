本地macos测试使用kong
---------------------------
+ 首先安装minikube （如果可以使用k3s会更加省资源）， -
    * 使用nix安装后启动失败 -
    * 使用homebrew安装失败 -
    * 使用二进制文件安装成功 +

使用docker启动minikube  `minikube start --driver=docker` -
* 使用homebrew安装multipass +

新建vm `multipass launch ~~name k3s ~~mem 1G --disk 5G`
