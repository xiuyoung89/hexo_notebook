---
title: Ubuntu 18.04 Install Shadowsockets-qt5(直接命令行安装)
date: 2019-02-13 18:53
tags:
---

# Ubuntu 18.04 Install Shadowsockets-qt5

1. 查看电脑环境

```bash
uname -a  #查看内核版本
Linux version 4.15.0-45-generic (buildd@lgw01-amd64-031) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019

lsb_release -a  #查看系统版本
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.2 LTS
Release:	18.04
Codename:	bionic

```

2. 安装shadowsockets-qt5

```bash
sudo add-apt-repository ppa:hzwhuang/ss-qt5
sudo apt-get update
sudo apt-get install shadowsocks-qt5
```

此时应该会报错，因为没有没有18.04的安装源，查看[shadowsockets-qt5安装源介绍](https://code.launchpad.net/~hzwhuang/+archive/ubuntu/ss-qt5)

3. 手动修改
   
由于shadowsockets-qt5作者并没有及时更新最新的版本，但是作者网站中有介绍，可以手动修改hzwhuang-ubuntu-ss-qt5-bionic.list中的系统版本。

```bash
    cd /etc/apt/sources.list.d
    #修改为
    deb http://ppa.launchpad.net/hzwhuang/ss-qt5/ubuntu artful main
    # deb-src http://ppa.launchpad.net/hzwhuang/ss-qt5/ubuntu artful main
    #更新一下源：
    sudo apt-get update
    #再次安装：
    sudo apt-get install shadowsocks-qt5

```



