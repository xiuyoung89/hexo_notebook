# Ubuntu 18.04 搭建 Trojan 代理服务器 + BBR 加速


## 服务器环境

```bash
# sudo lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04 LTS
Release:	18.04
Codename:	bionic
```

## 安装 Trojan

> [github地址](https://github.com/trojan-gfw/trojan)
> 参考 地址 

根据README文档，选择快速安装

```bash
sudo bash -c "$(curl -fsSL https://raw.githubusercontent.com/trojan-gfw/trojan-quickstart/master/trojan-quickstart.sh)"

```

