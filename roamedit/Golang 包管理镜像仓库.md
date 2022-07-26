Golang 包管理镜像仓库
---------------------------

Golang 包管理镜像仓库
   :PROPERTIES:
   :CUSTOM_ID: golang-包管理镜像仓库
   :END:
事实上在golang 1.11版本推出go
mod的同时，还推出了一个新的环境变量GOPROXY，它的作用类似http(s)_proxy，用于为golang代码仓库做镜像代理。

有了这个变量，我们只需要再找一个稳定可靠的镜像仓库就可以了。 *
jfrog提供的GoCenter就是这样一个镜像仓库。 *
使用方法非常简单，配置环境变量即可: * export GOPROXY=https://gocenter.io

以kube-role-finder为例，编译命令为

GOPROXY="https://gocenter.io" GO111MODULE=on go build *
注意，GOPROXY开启以后，若失败不会自动回源。
