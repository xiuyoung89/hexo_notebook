配置文件路径： /home/<username>/.bitcoin/bitcoin.conf

```json
testnet=1
txindex=1

# rpcthread 
rpcthreads=64       # 线程数量
dbcache=3000        # MB

server=1
datadir=/home/ubuntu/btc-testnet-node
rpcuser=user
rpcpassword=password
rpcport=18545
rpcallowip=0.0.0.0/0
```


重新解析btc数据库

export http_proxy=http://192.168.0.141:8123