# centos deploy chain-server

1. install node

本地开发环境版本v10.15.3,避免开发版本导致的异常，所有官网寻找制定版本[下载](https://nodejs.org/en/download/releases/)。
```bash
node --version
# v10.15.3 
```

```bash
wget https://nodejs.org/download/release/v10.15.3/node-v10.15.3-linux-x64.tar.gz
tar -xvzf node-v10.15.3-linux-x64.tar.gz

# 方法1:软链接
sudo ln -s /home/centos/tools/node-v10.15.3-linux-x64/bin/node /usr/bin/node
sudo ln -s /home/centos/tools/node-v10.15.3-linux-x64/bin/npm /usr/bin/npm
sudo ln -s /home/centos/tools/node-v10.15.3-linux-x64/bin/npx /usr/bin/npx

# 方法2: 把node/bin目录添加到path下，这样npm install -g安装的文件可以直接用
# 1. 临时生效   export
# 2. 当前用户生效 vim ~/.bash_profile
# 3. 所有用户生效 vim /etc/profile
```