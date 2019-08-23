# 使用Docker启动geth同步节点

## docker install geth

```bash
sudo docker search ethereum

# ethereum/client-go         Official golang implementation of the Ethere…   187                             [OK]

sudo docker install  ethereum/client-go

# 查看是否安装成功

sudo docker images

#REPOSITORY           TAG                 IMAGE ID            CREATED             SIZE
#ethereum/client-go   latest              34d54ea9fffd        4 hours ago         48MB

```

## 启动镜像

```bash
sudo docker run  -it --name eth-node -v /home/ubuntu/eth-ropsten-node:/root/.ethereum \
           -p 8545:8545 -p 30303:30303 -p 8200:8200\
           ethereum/client-go --rpc --rpcaddr "0.0.0.0" --syncmode "fast"\
            --rpcapi "personal,db,eth,net,web3" --cache 2048 --testnet console
```

/home/ubuntu/eth-ropsten-node