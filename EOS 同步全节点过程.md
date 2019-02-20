---
title: 'EOS 同步节点的配置跟步骤'
author: wangxiuyoung
date: 2019-02-18
---

# EOS 同步节点的配置

根据官网给出最新的同步方法：

1. Ubuntu 18.04 Debian Package Install

```bash
wget https://github.com/eosio/eos/releases/download/v1.6.2/eosio_1.6.2-1-ubuntu-18.04_amd64.deb
sudo apt install ./eosio_1.6.2-1-ubuntu-18.04_amd64.deb
```
此时已经安装完成，验证方式：
```bash
nodeos --version #v1.6.1
```
1. Quick Start

check [p2p server nodes](https://eosnodes.privex.io/?config=1)

```bash
wget https://eosnodes.privex.io/static/genesis.json
nodeos --genesis-json genesis.json
# press ctrl-c once it's loaded the genesis to exit nodeos

nano ~/.local/share/eosio/nodeos/config/config.ini
# place some p2p nodes in here, you can get them in config format from the link at the top of this page

# add plugin in config.ini
# plugin = eosio::chain_api_plugin
# plugin = eosio::history_api_plugin
# plugin = eosio::chain_plugin
# plugin = eosio::history_plugin
# plugin = eosio::net_plugin
# plugin = eosio::net_api_plugin

# now start it for real

nodeos

# if you get something like "failed to initialize", clear your blocks/state and re-run against genesis

rm ~/.local/share/eosio/nodeos/data/blocks/* -r
rm ~/.local/share/eosio/nodeos/data/state/* -r

nodeos --genesis-json genesis.json

# this is just a quickstart guide, you should understand how to run this in the background etc. and how to configure it

# now to grab your account, use eosauthority.com and put in your ICO eth address to find your generated name
# once you have that, you can import your key and register your account like this:

cleos wallet create
# write down the password somewhere safe

cleos unlock

cleos import YOUR_EOS_PRIVKEY

cleos system newaccount --stake-net "0.1000 EOS" --stake-cpu "0.1000 EOS" --buy-ram-kbytes 8 YOURGENERATEDNAME THE_NAME_YOU_WANT NEW_PUBKEY
```




Genesis File (put in genesis.json and launch nodeos with --genesis-json genesis.json)
```json
{
  "initial_timestamp": "2018-06-08T08:08:08.888",
  "initial_key": "EOS7EarnUhcyYqmdnPon8rm7mBCTnBoot6o7fE2WzjvEX2TdggbL3",
  "initial_configuration": {
    "max_block_net_usage": 1048576,
    "target_block_net_usage_pct": 1000,
    "max_transaction_net_usage": 524288,
    "base_per_transaction_net_usage": 12,
    "net_usage_leeway": 500,
    "context_free_discount_net_usage_num": 20,
    "context_free_discount_net_usage_den": 100,
    "max_block_cpu_usage": 200000,
    "target_block_cpu_usage_pct": 1000,
    "max_transaction_cpu_usage": 150000,
    "min_transaction_cpu_usage": 100,
    "max_transaction_lifetime": 3600,
    "deferred_trx_expiration_window": 600,
    "max_transaction_delay": 3888000,
    "max_inline_action_size": 4096,
    "max_inline_action_depth": 4,
    "max_authority_depth": 6
  }
}
```

参考：
[EOS 学习框架整理](https://www.jianshu.com/p/74db8f0b055d)
[EOS环境搭建与同步主网记录](https://zhuanlan.zhihu.com/p/49984105)