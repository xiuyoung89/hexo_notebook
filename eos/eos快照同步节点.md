---
title: eos + ubuntu18.04 快照同步节点
date: 2019-10-17
author: young
---

# EOS 快照同步节点


## 下载安装EOSIO

1. [官网下载最新版本](https://github.com/EOSIO/eos)

```bash
wget https://github.com/eosio/eos/releases/download/v1.8.5/eosio_1.8.5-1-ubuntu-16.04_amd64.deb
sudo dpkg -i  eosio_1.8.5-1-ubuntu-16.04_amd64.deb
```

2.  查看版本

```bash
eos nodeos --version      
# v1.8.5
```

## 配置EOS节点

1. 创建EOS工作目录

```bash
mkdir eos-chain-node
```

2. 下载创始块

```bash
wget https://raw.githubusercontent.com/CryptoLions/EOS-MainNet/master/genesis.json
```

3. 下载主网配置文件

```bash
wget https://raw.githubusercontent.com/CryptoLions/EOS-MainNet/master/config.ini
```

4. 下载最新可用节点清单

```bash
wget https://eosnodes.privex.io/?config=1 -O peers.txt
```

5. 更新主网配置文件中的节点列表

在配置文件config.ini中，找到所有的p2p-peer-address配置项，例如：
```bash
p2p-peer-address = bp.cryptolions.io:9876
```
然后用peers.txt中的内容替换。


## 启动EOS节点同步

1. 第一次启动节点

```bash
nodeos --config-dir . --data-dir . --genesis-json genesis.json --delete-all-blocks

```
打开新的terminal 然后查看同步节点信息

```bash
cleos get info
```
输出结果:

```json
{
  "server_version": "7c0b0d38",
  "chain_id": "aca376f206b8fc25a6ed44dbdc66547c36c6c33e3a119ffbeaef943642f0e906",
  "head_block_num": 85334280,
  "last_irreversible_block_num": 85333953,
  "last_irreversible_block_id": "051617c198ba3b98542b7a3171719e213910a4cacde728189e0ef396e4c5500d",
  "head_block_id": "05161908b3dc30dd0fe829ace70ebd469c5ef1cc904a816df02d9eda82e830fe",
  "head_block_time": "2019-10-19T08:20:55.000",
  "head_block_producer": "eosiosg11111",
  "virtual_block_cpu_limit": 200000000,
  "virtual_block_net_limit": 1048576000,
  "block_cpu_limit": 200000,
  "block_net_limit": 1048576,
  "server_version_string": "v1.8.4",
  "fork_db_head_block_num": 85334280,
  "fork_db_head_block_id": "05161908b3dc30dd0fe829ace70ebd469c5ef1cc904a816df02d9eda82e830fe"
}
```


## EOS节点的停止与重新使用快照启动

1. 先关闭原来的进程nodeos，使用命令关闭而非强制关闭

```bash
pkill nodeos
```

2. 清理原来的数据

```bash
rm -rf blocks state
```

3. 首先在[eos node tools 官网下载](https://eosnode.tools/blocks) 最新的快照

```bash
wget $(wget --quiet "https://eosnode.tools/api/snapshots?limit=1" -O- | jq -r '.data[0].s3') -O snapshot.tar.gz

```

下载之后，将其解压

```bash
tar xvzf snapshot.tar.gz
```

4. 重新使用快照同步节点

```bash
nodeos  --config-dir . --data-dir . --genesis-json genesis.json --delete-all-blocks --snapshot ./snapshots/snapshot-05136c51d1f0eb421f7a3c5b3de8d4e17a398a7c60926985202bd0e7d018fee8.bin
```
