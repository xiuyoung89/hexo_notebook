# 直接二进制安装
1. [官网下载](https://nodejs.org/zh-cn/download/)
2. 解压
```bash
    tar xvf node-v11.10.0-linux-x64.tar.xz node-v11.10.0-linux-x64/
```
3. 直接进入目录查看node版本
```bash
    cd node-v11.10.0-linux-x64/bin
    ./node --version    #v11.10.0
```
4. 添加环境变量
   两种方式：一种就是直接把bin文件下的node根npm可执行文件直接软链接到系统bin目录下；一种是修改环境变量文件，把node文件添加到环境变量中。

   方法一：
   ```bash
   sudo ln -s /home/wangy/node/bin/node /usr/local/bin/node
   sudo ln -s /home/wangy/node/bin/npm /usr/local/bin/npm
   ```

   方法二：
   ```bash
    vim /etc/profile
	
    # 在底部添加
    export NODE_HOME=/opt/nodejs/node-v11.1.0-linux-x64/bin
    export PATH=$NODE_HOME:$PATH

    #激活修改
    source /etc/profile

    # 验证
    node -v
    npm -v

    # 如果全局安装pm2包，可以验证
    pm2 list
   ```