<!--
 * @title: Do not edit
 * @date: YYYY-MM-DD HH:mm:ss
 * @author: Young
 -->
下载acme.sh

```bash
apt-get install socat -y && curl https://get.acme.sh | sh
```

申请证书

```bash
sudo ~/.acme.sh/acme.sh --issue --nginx -d "*.nervousness.com" -k ec-256 --log --reloadcmd "systemctl reload trojan || true"

```

sudo ~/.acme.sh/acme.sh --issue  --re--nginx -d nervousness.com  -d www.nervousness.online -d trojan.nervousness.online -d blog.nervousness.online -d api.nervousness.online -k ec-256 --log 

acme.sh --issue --nginx -d nervousness.com  -d www.nervousness.online -d trojan.nervousness.online -d blog.nervousness.online -d api.nervousness.online -k ec-256

acme.sh  --issue    -d nervousness.online -d *.nervousness.online

生成证书

```bash
sudo ~/.acme.sh/acme.sh --installcert   -d trojan.nervousness.online --fullchainpath /etc/trojan/trojan.crt --keypath /etc/trojan/trojan.key --ecc
```