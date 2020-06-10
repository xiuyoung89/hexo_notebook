<!--
 * @title: Do not edit
 * @date: YYYY-MM-DD HH:mm:ss
 * @author: Young
--> 
# SSH Config 管理

## 配置文件


```bash
用户配置文件 (~/.ssh/config)
系统配置文件 (/etc/ssh/ssh_config)
```

## 常用配置参数

* Host 别名
* HostName 主机名
* Port 端口
* User 用户名
* IdentityFile 密钥文件的路径
* IdentitiesOnly 只接受SSH key 登录
* PreferredAuthentications 强制使用Public Key验证
* ProxyCommand 代理配置

## Demo
```bash
Host nervusness
    HostName 67.218.141.175
    Port 28929
    User root
    ProxyCommand nc -X 5 -x 127.0.0.1:1081 %h %p
```

