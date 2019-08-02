# mysql error

## 1. Errcode: 24 - Too many open files

```bash
sudo mkdir /etc/systemd/system/mysql.service.d
sudo vi /etc/systemd/system/mysql.service.d/override.conf
Added this in the new file override.conf:

[Service]
LimitNOFILE=5000
Then restarted the service:

sudo systemctl daemon-reload
sudo systemctl restart mysql
```



## Errcode: 24 - Too many open files (centos)

```bash
vim  /etc/systemd/system/mysql.service

# 查看链接
# https://dbalife.info/2018/06/27/MySQL%E4%B8%AD%E7%9A%84open-files-limit/
```