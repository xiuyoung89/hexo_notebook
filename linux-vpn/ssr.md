
# ssr server

rus.51ssr.club
hk3.51ssr.club 
sg.51ssr.club
los.51ssr.club
jp.51ssr.club
tw.51ssr.club
usa.51ssr.club
端口 63944
密码信息20190604Wxy
加密方式chacha20
协议插件auth_sha1_v4
混淆插件tls1.2_ticket_auth


## ssr work config

```bash
{
    "server": "rus.51ssr.club",
    "server_ipv6": "::",
    "server_port": 63944,
    "local_address": "127.0.0.1",
    "local_port": 1080,

    "password": "20190604Wxy",
    "method": "chacha20",
    "protocol": "auth_sha1_v4",
    "protocol_param": "",
    "obfs": "tls1.2_ticket_auth",
    "obfs_param": "",
    "speed_limit_per_con": 0,
    "speed_limit_per_user": 0,

    "additional_ports" : {}, // only works under multi-user mode
    "additional_ports_only" : false, // only works under multi-user mode
    "timeout": 120,
    "udp_timeout": 60,
    "dns_ipv6": false,
    "connect_verbose_info": 0,
    "redirect": "",
    "fast_open": false
}

```

## myvpn 

```bash
// self vpn server 
{
    "server": "67.218.141.175",
    "server_ipv6": "::",
    "server_port": 1856,
    "local_address": "127.0.0.1",
    "local_port": 1080,

    "password": "www.eosdroping.com",
    "method": "aes-256-cfb",
    "protocol": "origin",
    "protocol_param": "",
    "obfs": "plain",
    "obfs_param": "",
    "speed_limit_per_con": 0,
    "speed_limit_per_user": 0,

    "additional_ports" : {}, // only works under multi-user mode
    "additional_ports_only" : false, // only works under multi-user mode
    "timeout": 120,
    "udp_timeout": 60,
    "dns_ipv6": false,
    "connect_verbose_info": 0,
    "redirect": "",
    "fast_open": false
}
```
