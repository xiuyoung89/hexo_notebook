---
    title:  "Docker学习笔记"
    date:   2019-02-19
---

# Docker学习笔记

## Docker 环境设置代理

1.设置docker代理
这里你首先要有一个HTTP代理可用，可参考ubuntu代理搭建

2.创建目录/etc/systemd/system/docker.service.d
```bash
cd /etc/systemd/system/
sudo mkdir docker.service.d
```

3.在该目录下创建文件 http-proxy.conf，在文件中添加配置：
```json
[Service]
Environment="HTTP_PROXY=http://192.168.8.186:8087/"
Environment="HTTPS_PROXY=http://192.168.8.186:8087/"
```

4.刷新配置,重启docker服务
```bash
sudo systemctl daemon-reload
sudo service docker restart
```

## Ubuntu Docker 启动

```bash
sudo docker pull ubuntu:18.04
sudo docker run -it --rm ubuntu:18.04 bash
```