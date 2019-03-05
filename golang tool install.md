---
title: "golang tools install"
data: "2019-03-05"
author: "xiuyoung"
---

# 安装golang

```bash
    sudo apt-get install golang
```

# 配置环境

```bash
#已经配置好的环境
go env
# GOARCH="amd64"
# GOBIN="/home/wangy/work/goproject/bin"
# GOCACHE="/home/wangy/.cache/go-build"
# GOEXE=""
# GOHOSTARCH="amd64"
# GOHOSTOS="linux"
# GOOS="linux"
# GOPATH="/home/wangy/work/goproject"
# GORACE=""
# GOROOT="/usr/lib/go"
# GOTMPDIR=""
# GOTOOLDIR="/usr/lib/go/pkg/tool/linux_amd64"
# GCCGO="gccgo"
# CC="gcc"
# CXX="g++"
# CGO_ENABLED="1"
# CGO_CFLAGS="-g -O2"
# CGO_CPPFLAGS=""
# CGO_CXXFLAGS="-g -O2"
# CGO_FFLAGS="-g -O2"
# CGO_LDFLAGS="-g -O2"
# PKG_CONFIG="pkg-config"
# GOGCCFLAGS="-fPIC -m64 -pthread -fmessage-length=0 -fdebug-prefix-map=/tmp/go-build632023567=/tmp/go-build -gno-record-gcc-switches"
```

## 配置步骤：

1. vim /etc/profile
2. 添加下边内容之末尾
   ```bash
    # golang  /home/wangy/work/goproject 这个文件自己创建，默认GOPATH 路径在～/go，可以通过go env 查看
    export GOROOT=/usr/lib/go
    export GOPATH=/home/wangy/work/goproject
    export GOBIN=/home/wangy/work/goproject/bin
    export GOLIB=/home/wangy/work/goproject
    export PATH=$PATH:$GOBIN:$GOPATH/bin:$GOROOT/bin
   ```
3. 使配置生效
   ```bash
   source /etc/profile      #或者直接重启电脑
   ```
4. 安装golang tools
   [官方给的安装方式](https://github.com/Microsoft/vscode-go/wiki/Go-tools-that-the-Go-extension-depends-on)正常情况下，安装会失败，就是我们大帝国的局域网，我本人绿色上网，配置代理也不能正常安装。只能一通google，原来这个问题已经有解决办法，我先把链接贴出来，不想看[链接](https://github.com/golang/lint/issues/288)跟着下边的方法安装也是可以的。
   ```bash
    mkdir -p $GOPATH/src/golang.org/x
    cd $GOPATH/src/golang.org/x
    git clone https://github.com/golang/tools.git
    git clone https://github.com/golang/lint.git
    #完成以上步骤后，执行
    go get golang.org/x/lint/golint
    #成功安装golint ，亲测有效
    #或者打开vscode，让vscode自行安装，应该也能成功
   ```
