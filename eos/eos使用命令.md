# EOS 发行属于自己的Token

>  部署代币合约

```bash
#测试网络中需要的
cleos create account eosio eosio.token EOS7ygonVZfE21a3KDE2VrEGBZFTPYaLJukaguCytUCwVvfDekLk6 EOS7ygonVZfE21a3KDE2VrEGBZFTPYaLJukaguCytUCwVvfDekLk6
```

## 正式网络中发行代币

1. 
PW5HtskHLF8bqK111atkLMDxRGzacbhRw26ZcWfJqnA6Bwfr6eG6S


cleos push action eosio.token create '[ "eosio", "100000000000.0000 EOSBYS", 0, 0, 0]' -p eosio.token

## 创建账号

1. 生成key-pair

```bash
cleos create key --to-console
```
2.  生成account

``bash
cleos -u  http://peer1.eoshuobipool.com:8181 system newaccount --stake-net '0.01 EOS' --stake-cpu '0.01 EOS' --buy-ram-kbytes 3 gteiocapital  gtecapital11 EOS8FzjvnfTytz7BL5TRkmri8hLWd2512MS8mvu1cfMFfgeLwRV5K EOS8FzjvnfTytz7BL5TRkmri8hLWd2512MS8mvu1cfMFfgeLwRV5K
```


cleos -u  http://peer1.eoshuobipool.com:8181  create account eosio eosio.token EOS7ygonVZfE21a3KDE2VrEGBZFTPYaLJukaguCytUCwVvfDekLk6 EOS7ygonVZfE21a3KDE2VrEGBZFTPYaLJukaguCytUCwVvfDekLk6

cleos  -u  http://peer1.eoshuobipool.com:8181  create account eosio eosio.token EOS6NbqQVXzVHuJdJfhtvsQ1muEy2VsoFrAweuBFfY1RWuG3Dw6MF EOS6NbqQVXzVHuJdJfhtvsQ1muEy2VsoFrAweuBFfY1RWuG3Dw6MF

cleos  createcle eosio eosio.token EOS6NbqQVXzVHuJdJfhtvsQ1muEy2VsoFrAweuBFfY1RWuG3Dw6MF EOS6NbqQVXzVHuJdJfhtvsQ1muEy2VsoFrAweuBFfY1RWuG3Dw6MF
