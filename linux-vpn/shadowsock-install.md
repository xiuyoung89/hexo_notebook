# shadowsock 使用相关

## shadows-client 安装使用
[参考文档](在Linux终端使用SSR服务实现科学上网)

1. 下载配置

```bash
# 需要本地git 环境
yum install -y git
git clone https://github.com/SAMZONG/gfwlist2privoxy.git
cd gfwlist2privoxy/
mv ssr /usr/local/bin
chmod +x /usr/local/bin/ssr
```

2. 安装配置

```bash
[root@localhost ~]# ssr install
Cloning into '/usr/local/share/shadowsocksr'...
remote: Counting objects: 5490, done.
remote: Total 5490 (delta 0), reused 0 (delta 0), pack-reused 5490
Receiving objects: 100% (5490/5490), 1.71 MiB | 410.00 KiB/s, done.
Resolving deltas: 100% (3799/3799), done.

[root@localhost ~]# ssr config 		# 配置文件路径 /usr/local/share/shadowsocksr/config.json
{
    "server": "0..0.0.0",	// ssr服务器ip
    "server_ipv6": "::",
    "server_port": 8080,	// ssr服务器端口
    "local_address": "127.0.0.1",
    "local_port": 1080,

    "password": "123456",		// 对应password
    "method": "none",			// 这里对应SSGlobal配置中的Encryption
    "protocol": "auth_chain_a",		//对应protocl
    "protocol_param": "",
    "obfs": "http_simple",		//对应obfs
    "obfs_param": "hello.world",	//对应obfs_param
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

3. 使用命令
```bash
ssr help
# ShadowSocksR python client tool
# if you have not install ssr, please run "ssr install"
# Usage:
#          ssr help
#          ssr config : edit config.json
#          ssr install : install shadowsocksr client
#          ssr uninstall : uninstall shadowsocksr client
#          ssr start : start the shadowsocks service
#          ssr stop : stop the shadowsocks service
#          ssr log : cat the log of shadowsocks
```