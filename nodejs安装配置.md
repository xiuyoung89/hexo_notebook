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
5. npm 设置代理 参考原文链接[https://medium.com/@jamesjefferyuk/how-to-use-npm-behind-a-socks-proxy-c81d6f51dff8](https://medium.com/@jamesjefferyuk/how-to-use-npm-behind-a-socks-proxy-c81d6f51dff8) 
   
   1. install polipo 
        In this guide I will show you how to turn your SOCKS proxy into a HTTP proxy to use npm. This has been tested on Ubuntu Xenial Xerus but should work fine on other Linux distributions.
        ```
        大概翻译了下就是把 socks5 代理转成http代理。(自己测试直接设置socks代理是没用)
        ```


        ```bash
        sudo apt-get install polipo
        ```

    2. edit config:    vim /etc/polipo/config and add the following lines:

        ```bash
        socksParentProxy = “127.0.0.1:1337”
        socksProxyType = socks5
        proxyAddress = “::0”
        proxyPort = 8123
        ```

    3. restart polipo
        ```bash
        sudo service polipo restart
        ```

    4. 保证 socks5 proxy 已经启动，后续补充

    5. 设置npm config
        ```bash
        npm config set proxy http://127.0.0.1:8123
        npm config set https-proxy http://127.0.0.1:8123
        ```

