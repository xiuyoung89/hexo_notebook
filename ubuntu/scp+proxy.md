# scp 代理形式拷贝

```bash
scp -o "ProxyCommand=nc -X connect -x 127.0.0.1:1080 %h %p"  filename  username@target_ip:/target_path
```

> demo

```bash
scp -o "ProxyCommand=nc -X connect -x 127.0.0.1:1080 %h %p"  -r /home/young/mnt/work/域名证书/nervousness  root@67.218.141.175:/root/trojan/cer
```
