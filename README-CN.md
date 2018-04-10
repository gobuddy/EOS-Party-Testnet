# 欢迎来到 EOS Party 测试网络.

[English](README.md)

EOS Party 测试网络是由EOS中文社区基于 `EOS DAWN 3.0` 组织创建的测试网络，该测试网络旨在为开发者提供更好的线上开发环境．

## 加入 EOS Party 测试网络

任何个人,组织都可以加入`EOS Party`成为BP,加入 `EOS Party` 测试网络成为BP需要以下几个步骤：

- 自己的服务器
- EOS环境搭建(建议使用Docker)
- 向社区提出申请(或者Github发起PR或Issues)

### 自己的服务器

作为EOS节点要为网络提供稳定的产生区块，所以需要参与者有稳定的服务器，基础服务器参考配置：   

  - CPU:2核
  - 内存:8G
  - 磁盘：40G

### EOS环境搭建(Docker快速部署)

确保你的服务器已经安装`Docker`和`Docker-Compose`, `Docker-Compose`不是必须.

- `mkdir -p /data/eos` 创建你的EOS节点数据存储的目录, 也可以是其他目录.
- 将[config.ini](config.ini)拷贝到`/data/eos` 并修改四处地方.
  - p2p-server-address: 改成你自己的服务器IP和监听的p2p端口, 默认是 IP:9876
  - agent-name: 改成你自己的标识, 域名或其他.
  - private-key: 你的密钥对, 建议[创建](https://eosfans.io/tools/generate/)全新的.
  - producer-name: 节点账户名(不需要你生成, 随便填一个即可).
- 将[genesis.json](genesis.json)文件拷贝到`/data/eos`目录, 不需要修改.

```
docker run -d \
    --restart=always \
    --name party \
    -V /data/eos:/opt/eosio/bin/data-dir \
    -p 8888:8888 \
    -p 9876:9876 \
    eosfans/eos:3.0.0 nodeosd.sh
```

启动节点.

`docker logs -f party` 查看日志.

### 向我们提出申请

如果你上面一步顺利完成的话, 应该能连接到Party的测试网络, 但是你的节点还不会生产块.

你需要向我们提供配置文件中`private-key`的公钥(只需要公钥)和`producer-name`的值.

然后我们手动将你添加仅BP列表.

你可以给当前项目提PR或者Issues,也可以在我们社区`https://eosfans.io/topics/260`留言.

我们添加成功后, 你的节点应该就可以自动生产区块了, 不需要变动或重启.
