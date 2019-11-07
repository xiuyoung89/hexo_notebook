# EOS 多节点私链搭建

1. 下载最新代码

```bash
# 自行编译
git clone  https://github.com/EOSIO/eos.git --recusive

git clone https://github.com/EOSIO/eosio.contracts.git --recusive

git clone  https://github.com/EOSIO/eosio.cdt.git -recusive
```

2. 启动创始块节点

```bash

# 第一次代带创始块启动
./nodeos -d /home/young/mnt/work/chain-node/bys/bys01-node -c /home/young/mnt/work/chain-node/bys/bys01-node/config.ini --genesis-json /home/young/mnt/work/chain-node/bys/bys01-node/genesis.json

# 不带创始块配置启动
./nodeos -d /home/young/mnt/work/chain-node/bys/bys01-node -c /home/young/mnt/work/chain-node/bys/bys01-node/config.ini
```

创始块有几个地方必须修改
>> 修改eosio的key,其中代码部分还需要修改，目录 /eos/CMakeLists.txx 中的 EOSIO_ROOT_KEY 也要修改成自己的key
```conf
{
  "initial_timestamp": "2018-06-08T08:08:08.888",
  "initial_key": "EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV",  #####必须是 eosio 节点 的 公钥
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
>>  修改配置config.ini

```conf
producer-name = eosio
signature-provider = EOS5DAUpjNHjoJotHEbFXhgc8AiLhf7vpt3ujfivDjnL5ms2R6RR3=KEY:5KcqrGnABkzAtPhfHNVUaavyViszSTNDUJr5boDJGKKabfyjXRe

agent-name = bys01

#blocks-dir = "blocks"
chain-state-db-size-mb = 65536
reversible-blocks-db-size-mb = 2048
contracts-console = true # 只能eosio节点为true

http-server-address = 0.0.0.0:8888
p2p-listen-endpoint = 0.0.0.0:9876
p2p-server-address = 127.0.0.1:9876


http-validate-host = false
verbose-http-errors = true  
abi-serializer-max-time-ms = 2000  

chain-threads = 8
http-threads = 6

access-control-allow-origin = *
access-control-allow-headers = Origin, X-Requested-With, Content-Type, Accept
# access-control-max-age =
# access-control-allow-credentials = false

wasm-runtime = wabt

#produce-time-offset-us = 250000
last-block-time-offset-us = -300000


# Safely shut down node when free space remaining in the chain state database drops below this size (in MiB). (eosio::chain_plugin)
chain-state-db-guard-size-mb = 128 
# Safely shut down node when free space remaining in the reverseible blocks database drops below this size (in MiB). (eosio::chain_plugin) 
reversible-blocks-db-guard-size-mb = 2

p2p-max-nodes-per-host = 150

# actor-whitelist =
# actor-blacklist =
# contract-whitelist =
# contract-blacklist =
# filter-on =

# SSL
# Filename with https private key in PEM format. Required for https (eosio::http_plugin)
# https-server-address =
# Filename with the certificate chain to present on https connections. PEM format. Required for https. (eosio::http_plugin)
# https-certificate-chain-file =
# Filename with https private key in PEM format. Required for https (eosio::http_plugin)
# https-private-key-file =

allowed-connection = any

max-clients = 150
connection-cleanup-period = 30
network-version-match = 0
sync-fetch-span = 2000
enable-stale-production = true

pause-on-startup = false
max-transaction-time = 30
max-irreversible-block-age = -1
txn-reference-block-lag = 0

plugin = eosio::chain_api_plugin
plugin = eosio::history_plugin
plugin = eosio::history_api_plugin
plugin = eosio::chain_plugin

#plugin = net_plugin
#plugin = net_api_plugin

#p2p-peer-address =
#p2p-peer-address =
#p2p-peer-address =

#p2p-peer-address = 172.2.0.100:9876
#p2p-peer-address = 172.2.0.200:9876

#Other Pub BP nodes
#p2p-peer-address =
#p2p-peer-address =
```

几处一定要修改的地方:

producer-name = eosio
signature-provider = EOS5DAUpjNHjoJotHEbFXhgc8AiLhf7vpt3ujfivDjnL5ms2R6RR3=KEY:5KcqrGnABkzAtPhfHNVUaavyViszSTNDUJr5boDJGKKabfyjXRe
作为 eosio 账号需要配置稳定节点  contracts-console   为 true， signature-provider 需要配置超级节点的私钥

3. 创建系统账号，正常应该使用多套钥匙宝创建

```bash
# eosio.token
./cleos create account eosio eosio.token EOS5qREcmiMJADMip7puq8aTs7hwMfij7jcekYHjbv1hvv6ytkXGH

# eosio.bpay 
./cleos create account eosio eosio.bpay EOS5zV67Pe3kV1ysecffoH9rb3TTfazPDVNgMnP1wVdfKpRxprGU7

# eosio.msig
./cleos create account eosio eosio.msig EOS65Wz62Aw99ViLU6KP9cf9ErGLpyk2wtBSsLep4YdV94DixwWT9

# eosio.names
./cleos create account eosio eosio.names EOS6AkKhjPKqbos6Virpuy4BXSjsWud1dHMjwF4Xw9CYxR957HhVp

# eosio.ram
./cleos create account eosio eosio.ram EOS7FswuQvgU5qoZkVzG4Psi9F4JtbvkhUnVJt7ee1xySRJU7mqwK

# eosio.ramfee 
./cleos create account eosio eosio.ramfee EOS7S3no9MV5mSYAZm3nknq7riEd4vFKzKMzSurH9zsb7b3zpWefW

# eosio.saving 
./cleos create account eosio eosio.saving EOS7wE2upXe7vpYhKUqr9h38Yz7QMtgr2LiLnwnr1mwtadztEBfKj

# eosio.stake 
./cleos create account eosio eosio.stake EOS81LEB6m3ZjnUCfc3tFqRZZcQv7V3rmW2ELEnc18WGhfEyNnruC

# eosio.vpay
./cleos create account eosio eosio.vpay EOS85H1YegJix4KTKAdQrAaf38WvekojazZzfQoRN17TjSK3DnzQY

# eosio.rex
./cleos create account eosio eosio.rex EOS6oiPnXbr4Hr8Py786CBhd9MG4CRr9CEkwGMuVhstDGWxs4T3z4

```

4.  部署系统合约并发行Token

```bash

#v1.8 版本部署合约需要参考 (issuse)[https://github.com/EOSIO/eos/issues/7180]

# bios contract
./cleos set contract eosio /home/young/mnt/work/git/eosio.contracts/build/contracts/eosio.bios

# 报错之后修改配置重新启动node
nodeos -d ./data --config-dir ./config --plugin eosio::chain_api_plugin --plugin eosio::producer_api_plugin -p eosio -e 2>stderr &

# 执行
curl -X POST http://127.0.0.1:8888/v1/producer/schedule_protocol_feature_activations -d '{"protocol_features_to_activate": ["0ec7e080177b2c02b278d5088611686b49d739925a92d9bfcacd7fc6b74053bd"]}' | jq

# 然后升级其他
./cleos set contract eosio /home/young/mnt/work/git/eosio.contracts/build/contracts/eosio.bios

./cleos push action eosio activate '["f0af56d2c5a48d60a4a5b5c903edfb7db3a736a94ed589d0b797df33ff9d3e1d"]' -p eosio # GET_SENDER
./cleos push action eosio activate '["2652f5f96006294109b3dd0bbde63693f55324af452b799ee137a81a905eed25"]' -p eosio # FORWARD_SETCODE
./cleos push action eosio activate '["8ba52fe7a3956c5cd3a656a3174b931d3bb2abb45578befc59f283ecd816a405"]' -p eosio # ONLY_BILL_FIRST_AUTHORIZER
./cleos push action eosio activate '["ad9e3d8f650687709fd68f4b90b41f7d825a365b02c23a636cef88ac2ac00c43"]' -p eosio # RESTRICT_ACTION_TO_SELF
./cleos push action eosio activate '["68dcaa34c0517d19666e6b33add67351d8c5f69e999ca1e37931bc410a297428"]' -p eosio # DISALLOW_EMPTY_PRODUCER_SCHEDULE
./cleos push action eosio activate '["e0fb64b1085cc5538970158d05a009c24e276fb94e1a0bf6a528b48fbc4ff526"]' -p eosio # FIX_LINKAUTH_RESTRICTION
./cleos push action eosio activate '["ef43112c6543b88db2283a2e077278c315ae2c84719a8b25f25cc88565fbea99"]' -p eosio # REPLACE_DEFERRED
./cleos push action eosio activate '["4a90c00d55454dc5b059055ca213579c6ea856967712a56017487886a4d4cc0f"]' -p eosio # NO_DUPLICATE_DEFERRED_ID
./cleos push action eosio activate '["1a99a59d87e06e09ec5b028a9cbb7749b4a5ad8819004365d02dc4379a8b7241"]' -p eosio # ONLY_LINK_TO_EXISTING_PERMISSION
./cleos push action eosio activate '["4e7bf348da00a945489b2a681749eb56f5de00b900014e137ddae39f48f69d67"]' -p eosio # RAM_RESTRICTIONS
# token contract
./cleos set contract eosio.token /home/young/mnt/work/git/eosio.contracts/build/contracts/eosio.token

# msig contract 
./cleos set contract eosio.msig  /home/young/mnt/work/git/eosio.contracts/build/contracts/eosio.msig

./cleos push action eosio.token create '["eosio", "27000000000.0000 BYS",0,0,0]' -p eosio.token
./cleos push action eosio.token issue '["eosio", "27000000000.0000 BYS", "issue"]' -p eosio


# 部署 system 合约 需要注意的 新版本EOS
# v1.8

# 使用失败
./cleos push action eosio init '[0,"4,BYS"]' -p eosio@active
./cleos  set contract eosio /home/young/mnt/work/git/eosio.contracts/build/contracts/eosio.system/ 
# ./cleos  push action eosio setpriv '["eosio.msig", 1]' -p eosio@active
```

5. 创建账号

```bash
# bysnode1
./cleos system newaccount --transfer  eosio bysnode1 EOS8QG34GR99U6WYCmYVtFYxHLEG1k8d11GaphGyd2f4pqr2BAbgw --stake-net "1000 BYS" --stake-cpu "1000 BYS" --buy-ram "1000 BYS"   

#bysnode2
./cleos  system newaccount --transfer eosio bysnode2 EOS8ZEQsSK5tBHNFPUspgsBVpsk4Ad7QPonrL1ho7RAoVSGXwCJLp --stake-net "1000 BYS" --stake-cpu "1000 BYS" --buy-ram "1000 BYS" 

#bysnode3
./cleos  system newaccount --transfer eosio bysnode3 EOS78fN9NMQ24raZz5nTpDrEgvG1nJcNj5vPk6qb9GZqAD5UFd6Fb --stake-net "1000 BYS" --stake-cpu "1000 BYS" --buy-ram "1000 BYS" 

#bysuser1111
./cleos  system newaccount --transfer eosio bysuser1111 EOS5DUVCWMmn9aXSv1JZrRjuEnysrNXtSaZyBHSG5uDSe9RJCJmrG --stake-net "1000 BYS" --stake-cpu "1000 BYS" --buy-ram "1000 BYS"   

#bysuser2222
./cleos  system newaccount --transfer eosio bysuser2222 EOS6BuvLwBmptqZY9MmzVLH8jV8UQ1CnMTt25dRpZrCjcb2wkD3hp --stake-net "1000 BYS" --stake-cpu "1000 BYS" --buy-ram "1000 BYS"   
   
#bysuser3333
./cleos  system newaccount --transfer eosio bysuser3333 EOS58BBRG9TdnVqA26dLt6E6cqviF7ZgXpe1HBJjZmVmxBzrjbkK3 --stake-net "1000 BYS" --stake-cpu "1000 BYS" --buy-ram "1000 BYS"   
   

#bbb
./cleos  system newaccount --transfer eosio bbb EOS7YQP2MxbRbSqJJ89VZJBqs44biQkzqDQj3Cxb8hVaXWZdUYpcm --stake-net "1000 BYS" --stake-cpu "1000 BYS" --buy-ram "1000 BYS" 

#ccc
./cleos  system newaccount --transfer eosio ccc EOS8b1DYUPTH6BE65jDxzqkP95PxwStoPqfV4VWHiZX5z2sR2rVJw --stake-net "1000 BYS" --stake-cpu "1000 BYS" --buy-ram "1000 BYS"  

#user1
./cleos  system newaccount --transfer eosio user1 EOS5Vz3XzoBEjbk99yZU31cijzdLcYdADvjxWMFAQu6beUBTwdjWV --stake-net "1000 BYS" --stake-cpu "1000 BYS" --buy-ram "1000 BYS"   

```

6. 启动别的节点

```bash
./nodeos -d /home/young/mnt/work/chain-node/bys/bys02-node -c /home/young/mnt/work/chain-node/bys/bys02-node/config.ini --genesis-json /home/young/mnt/work/chain-node/bys/genesis.json

./nodeos -d /home/young/mnt/work/chain-node/bys/bys03-node -c /home/young/mnt/work/chain-node/bys/bys03-node/config.ini --genesis-json /home/young/mnt/work/chain-node/bys/genesis.json

./nodeos -d /home/young/mnt/work/chain-node/bys/bys04-node -c /home/young/mnt/work/chain-node/bys/bys04-node/config.ini --genesis-json /home/young/mnt/work/chain-node/bys/genesis.json
```


7. 创建bys funder 

```bash
./cleos transfer eosio bysuser1111 "1500000000 BYS" "hello bysuser1111 founder."

./cleos transfer eosio bysuser2222 "1500000000 BYS" "hello bysuser2222 founder."

./cleos transfer eosio bysuser3333 "1500000000 BYS" "hello bysuser3333 founder."
```

8. 注册节点
```bash
# bysnode1
./cleos   system regproducer bysnode1 EOS8QG34GR99U6WYCmYVtFYxHLEG1k8d11GaphGyd2f4pqr2BAbgw

#bysnode2
./cleos   system regproducer bysnode2 EOS8ZEQsSK5tBHNFPUspgsBVpsk4Ad7QPonrL1ho7RAoVSGXwCJLp

#bysnode3
./cleos   system regproducer bysnode3 EOS78fN9NMQ24raZz5nTpDrEgvG1nJcNj5vPk6qb9GZqAD5UFd6Fb
```

9. 抵押资源

```bash
./cleos system  delegatebw bysuser1111 bysuser1111 "1000000000 BYS" "500000000 BYS"
./cleos system  delegatebw bysuser2222 bysuser2222 "1000000000 BYS" "500000000 BYS"
./cleos system  delegatebw bysuser3333 bysuser3333 "1000000000 BYS" "500000000 BYS"
```

10. 查看单个账号抵押资源的信息

```bash
./cleos get  account bysuser1111
```


11. 投票

```bash
./cleos system   voteproducer prods bysuser1111 bysnode1 bysnode2 bysnode3

./cleos system   voteproducer prods bysuser2222 bysnode1 bysnode2 bysnode3

./cleos system   voteproducer prods bysuser3333 bysnode1 bysnode2 bysnode3
```

12. 获取投票信息

```bash
# 查看当前所有节点的投票信息
./cleos system listproducers
```

取消抵押(待整理)

```bash
cleos -u http://172.18.0.1:8888 system undelegatebw user2  user2 '0.02 SYS' '0.02 SYS'
```
领取返还的token

```bash
cleos push action eosio refund '["本人账户名"]' -p 本人账户名
```

查询出块顺序

```bash
http://127.0.0.1:8888/v1/chain/get_producer_schedule
```