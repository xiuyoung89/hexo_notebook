<!--
 * @title: Do not edit
 * @date: YYYY-MM-DD HH:mm:ss
 * @author: Young
 -->
## 启动程序脚本
```bash
#!/bin/bash

pid=$(ps -ef | grep "ws-data-server" | grep -v grep | awk '{print $2}')

if [ -z "$pid" ];then
	cd /home/centos/work/
	nohup ./ws-data-server &
fi
```


## Cron 脚本跟命令

```bash
*/1 * * * * /home/centos/work/startup.sh
sudo crontab -ucentos -e
```