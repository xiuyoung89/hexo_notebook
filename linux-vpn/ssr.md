
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


server config 
```bash
# Congratulations, ShadowsocksR server install completed!
# Your Server IP        :  67.218.141.175 
# Your Server Port      :  1520 
# Your Password         :  www.eosdroping.com 
# Your Protocol         :  auth_chain_a 
# Your obfs             :  tls1.2_ticket_auth 
# Your Encryption Method:  chacha20 
```

检查端口跟ip是否已封
```bash
# http://tool.chinaz.com/port/
```

```bash
ssr://cnVzLjUxc3NyLmNsdWI6NjM5NDQ6YXV0aF9zaGExX3Y0OmNoYWNoYTIwOnRsczEuMl90aWNrZXRfYXV0aDpNakF4T1RBMk1EUlhlSGsvP3JlbWFya3M9NUwtRTU3Mlg1cGF2TFVFJmdyb3VwPVFVTnVaWFF0NXFDSDVZZUc1YVdYNmFTUTQ0Q1FPREJITC1hY2lPT0FrUQ|ssr://aGszLjUxc3NyLmNsdWI6NjM5NDQ6YXV0aF9zaGExX3Y0OmNoYWNoYTIwOnRsczEuMl90aWNrZXRfYXV0aDpNakF4T1RBMk1EUlhlSGsvP3JlbWFya3M9NmFhWjVyaXZMVU1nJmdyb3VwPVFVTnVaWFF0NXFDSDVZZUc1YVdYNmFTUTQ0Q1FPREJITC1hY2lPT0FrUQ|ssr://c2cuNTFzc3IuY2x1Yjo2Mzk0NDphdXRoX3NoYTFfdjQ6Y2hhY2hhMjA6dGxzMS4yX3RpY2tldF9hdXRoOk1qQXhPVEEyTURSWGVIay8_cmVtYXJrcz01cGF3NVlxZzVaMmhMVUVnJmdyb3VwPVFVTnVaWFF0NXFDSDVZZUc1YVdYNmFTUTQ0Q1FPREJITC1hY2lPT0FrUQ|ssr://cmMuNTFzc3IuY2x1Yjo2Mzk0NDphdXRoX3NoYTFfdjQ6Y2hhY2hhMjA6dGxzMS4yX3RpY2tldF9hdXRoOk1qQXhPVEEyTURSWGVIay8_cmVtYXJrcz01TC1FNTcyWDVwYXZMVUlnJmdyb3VwPVFVTnVaWFF0NXFDSDVZZUc1YVdYNmFTUTQ0Q1FPREJITC1hY2lPT0FrUQ|ssr://bG9zLjUxc3NyLmNsdWI6NjM5NDQ6YXV0aF9zaGExX3Y0OmNoYWNoYTIwOnRsczEuMl90aWNrZXRfYXV0aDpNakF4T1RBMk1EUlhlSGsvP3JlbWFya3M9NTc2TzVadTlMVUVnJmdyb3VwPVFVTnVaWFF0NXFDSDVZZUc1YVdYNmFTUTQ0Q1FPREJITC1hY2lPT0FrUQ|ssr://anAuNTFzc3IuY2x1Yjo2Mzk0NDphdXRoX3NoYTFfdjQ6Y2hhY2hhMjA6dGxzMS4yX3RpY2tldF9hdXRoOk1qQXhPVEEyTURSWGVIay8_cmVtYXJrcz01cGVsNXB5c0xVRWcmZ3JvdXA9UVVOdVpYUXQ1cUNINVllRzVhV1g2YVNRNDRDUU9EQkhMLWFjaU9PQWtR|ssr://ZXUuNTFzc3IuY2x1Yjo2Mzk0NDphdXRoX3NoYTFfdjQ6Y2hhY2hhMjA6dGxzMS4yX3RpY2tldF9hdXRoOk1qQXhPVEEyTURSWGVIay8_cmVtYXJrcz01cXluNXJTeUxVRWcmZ3JvdXA9UVVOdVpYUXQ1cUNINVllRzVhV1g2YVNRNDRDUU9EQkhMLWFjaU9PQWtR|ssr://c2cyLjUxc3NyLmNsdWI6NjM5NDQ6YXV0aF9zaGExX3Y0OmNoYWNoYTIwOnRsczEuMl90aWNrZXRfYXV0aDpNakF4T1RBMk1EUlhlSGsvP3JlbWFya3M9NXBhdzVZcWc1WjJoTFVJJmdyb3VwPVFVTnVaWFF0NXFDSDVZZUc1YVdYNmFTUTQ0Q1FPREJITC1hY2lPT0FrUQ|ssr://dHcuNTFzc3IuY2x1Yjo2Mzk0NDphdXRoX3NoYTFfdjQ6Y2hhY2hhMjA6dGxzMS4yX3RpY2tldF9hdXRoOk1qQXhPVEEyTURSWGVIay8_cmVtYXJrcz01WS13NXJtLUxVRWcmZ3JvdXA9UVVOdVpYUXQ1cUNINVllRzVhV1g2YVNRNDRDUU9EQkhMLWFjaU9PQWtR|ssr://aGsuNTFzc3IuY2x1Yjo2Mzk0NDphdXRoX3NoYTFfdjQ6Y2hhY2hhMjA6dGxzMS4yX3RpY2tldF9hdXRoOk1qQXhPVEEyTURSWGVIay8_cmVtYXJrcz02YWFaNXJpdkxVRSZncm91cD1RVU51WlhRdDVxQ0g1WWVHNWFXWDZhU1E0NENRT0RCSEwtYWN
```
