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