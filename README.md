[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/fanux/sealos)
[![Build Status](https://cloud.drone.io/api/badges/fanux/sealos/status.svg)](https://cloud.drone.io/fanux/sealos)
[![Go Report Card](https://goreportcard.com/badge/github.com/fanux/sealos)](https://goreportcard.com/report/github.com/fanux/sealos)

![](./arch.png)

# 快速开始

[官方文档](https://sealyun.com/docs)

> 环境信息

主机名|IP地址
---|---
master0|192.168.0.2 
master1|192.168.0.3 
master2|192.168.0.4 
node0|192.168.0.5 

服务器密码：123456

> 只需要准备好服务器，在任意一台服务器上执行下面命令即可

```sh
# 下载并安装sealos, sealos是个golang的二进制工具，直接下载拷贝到bin目录即可
wget https://github.com/fanux/sealos/releases/download/v3.0.1/sealos && \
    chmod +x sealos && mv sealos /usr/bin 

# 安装一个三master的kubernetes集群
sealos init --passwd 123456 \
	--master 192.168.0.2  --master 192.168.0.3  --master 192.168.0.4  \
	--node 192.168.0.5 \
	--pkg-url https://sealyun.oss-cn-beijing.aliyuncs.com/37374d999dbadb788ef0461844a70151-1.16.0/kube1.16.0.tar.gz \
	--version v1.16.0
```
> 参数含义

参数名|含义|示例
---|---|---
passwd|服务器密码|123456
master|k8s master节点IP地址| 192.168.0.2
node|k8s node节点IP地址|192.168.0.3
pkg-url|离线资源包地址，支持下载到本地，或者一个远程地址|/root/kube1.16.0.tar.gz
version|[资源包](http://store.lameleg.com)对应的版本|v1.16.0

# 特性

[x] 99年证书
[x] 不依赖ansible haproxy keepalved, 一个二进制工具，另依赖
[x] 离线安装，不同kubernetes版本下载对应不同版本的[资源包](http://store.lameleg.com)即可,离线包包含所有二进制文件配置文件和镜像
[x] 高可用通过ipvs实现的localLB，占用资源少，稳定可靠，类似kube-proxy的实现
[x] 几乎可兼容所有支持systemd的x86_64架构的环境
[x] 轻松实现集群节点的增加/删除
[x] 上千用户在线上环境使用sealos，稳定可靠
[x] 资源包放在阿里云oss上，再也不用担心网速
[x] dashboard ingress prometheus等APP 同样离线打包，一键安装
