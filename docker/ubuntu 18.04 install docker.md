<!--
 * @title: Do not edit
 * @date: YYYY-MM-DD HH:mm:ss
 * @author: Young
 -->
---
    title:  "ubuntu 18.04 install docker"
    date:   2019-05-20
    author: young
---
# Ubuntu 18.04 安装Docker CE 

## 首先设置Reposity

[官网参考链接](https://docs.docker.com/install/linux/docker-ee/ubuntu/)


1. 更新 apt package

```bash
    sudo apt-get update

```
2. 安装依赖的一些工具

```bash
    sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        software-properties-common
```
3. Add Docker’s official GPG key
```bash
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

    # OK
    
    # 检测命令
    apt-key list        

    # 需要看看 apt-key 信息
    # /etc/apt/trusted.gpg
    # --------------------
    # pub   rsa4096 2017-02-22 [SCEA]
    #     9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
    # uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
    # sub   rsa4096 2017-02-22 [S]
```

4. 添加稳定版本地址

```bash
    sudo add-apt-repository \
        "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
        $(lsb_release -cs) \
        stable"


    # 检测命令(可忽略)
    cat /etc/apt/sources.list | grep docker
    # deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
    # deb-src [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
```

## 开始正式安装

1. 安装前必要工作更新package
```bash
    sudo apt-get update
```

2. 安装
```bash
    sudo apt-get install docker-ce docker-ce-cli containerd.io

    # 检测命令(可忽略)
    # docker --version
    # Docker version 18.09.6, build 481bc77
```


可以直接下载deb安装，可参考官方文档,可以直接跳转下载对应的安装包。[跳转](https://download.docker.com/linux/ubuntu/dists/bionic/pool/stable/amd64/)

## 创建docker用户组，应用用户加入docker组

```bash
sudo groupadd docker

 sudo usermod -aG docker ${USER}

 sudo systemctl restart docker 
```

