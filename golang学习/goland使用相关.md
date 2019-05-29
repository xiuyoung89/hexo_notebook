

1. goland 中设置文件头信息

```bash
    /*
    @Time : ${DATE} ${TIME} 
    @Author : ${USER}
    @File : ${NAME}
    @Software: ${PRODUCT_NAME}
    */
    package ${GO_PACKAGE_NAME}
```

2. 常用快捷键


3. go mod使用教程

```bash
# export export GO111MODULE=auto 
# v1.12 之后默认 auto 具体
# 在 gopath 之外的路径下创建项目目录
mkdir go-test
go mod init go-test
```

4. go get 被墙的问题彻底修复 ubuntu系统

    > 首先电脑先配置翻墙，可以参考
自己系统使用的是 shadowsocks-qt5 [git地址](https://github.com/shadowsocks) 客户端，服务器应有尽有.

    现在已经配置好代理，我给系统设置代理
    ```bash
    export all_proxy=socks://127.0.0.1:1080
    ```

    但是这样配置之后go get 还是会超时。 wtf？！！！ 后来一通google发现是go get不使用socks5协议，那就是只能使用http协议代理。两种解决办法：
    方案一：把shadowsocks-qt5客户端的本地代理协议全部改成http协议；（因为自己本地git的配置还有浏览器的代理协议都设置的socks协议，所以这种方案对我来说不可行，那么寻找方案二了）
    方案二：给系统设置http代理，并把http转发给socks5(为什么这样做？ 我的理解：我的代理客户端现在设置的代理协议是socks5,端口是1080，就是所有的代理最终都是这个端口转发。上边设置all_proxy让终端走了代理，漏了http协议的处理，所以我现在给所有http的协议转成socks5协议，这时候需要使用 polimo工具了)
    ```bash
    sudo apt-get install polimo

    vim /etc/polipo/config # 文件不存在新建

    # 添加配置
    socksParentProxy = "127.0.0.1:1080"
    socksProxyType = socks5
    proxyAddress = "::0"
    proxyPort = 8123
    ```

    这样做是为了把 http：8123 的数据都通过 socks5:1080转发出去吗?

    然后重启 polimo 服务
    ```bash
    service polipo restart  #启动失败几代查看端口或者报错日志  service polipo restatus 应该能看到报错的日志
    ```

    然后再给终端设置代理

    ```bash
    http_proxy=http://127.0.0.1:8123
    ```

    然后 go get 完美!