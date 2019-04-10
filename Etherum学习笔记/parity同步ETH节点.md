--- 
title: parity同步ETH节点 ---
author: young
date:   2019-04-10
--- 

# Parity同步ETH节点



启动命令：
关键是开启ws访问方式
```bash
parity --chain=kovan --tx-gas-limit=8000000 --gasprice=10  --ws-interface=127.0.0.1 --ws-port=8546 --ui-no-validation --jsonrpc-apis web3,rpc

nohup parity --datadir=/mnt/ethdata --tx-gas-limit=8000000 --min-gas-price=2 --ws-interface=0.0.0.0 --ws-port=8546 --ui-no-validation --jsonrpc-apis=all > ./paritylog/20180907_001.log &
```


局域网本地：
```bash
parity --datadir=/home/wangxy/tmp  --jsonrpc-interface all --jsonrpc-cors all --jsonrpc-apis all --jsonrpc-hosts all --rpcport 18545  --ws-port 18546  --ws-interface all  --ws-apis all

# 相关参数介绍参考：
[https://wiki.parity.io/Configuring-Parity-Ethereum.html](https://wiki.parity.io/Configuring-Parity-Ethereum.html)

--no-warp


WebSock访问方式：

Web3Config.WebProvider = 'ws://127.0.0.1:8546';
var web3 = new Web3(new Web3.providers.WebsocketProvider(Web3Config.WebProvider));
```