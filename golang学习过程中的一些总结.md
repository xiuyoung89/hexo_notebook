---
    title: golang学习过程中的一些总结
    author: xiuyoung
    date: 2019-03-11
---

# golang新手学习过程中的总结

## 1.如何查找并安装需要的模块，例如http模块

google的结果是: http模块是内部模块，只不过应用方式应该是"net/http"不能直接引用"http"

## 2. http.Get("www.baidu.com")

error: fetch: Get www.baidu.com: unsupported protocol scheme ""
reason: Get的网址有误，应在其前面添加"http://"或"https://"，具体添加哪个要看你要打开的网站使用哪个协议
solution：http.Get("https://www.baidu.com") 

## 3. go mod 使用之前带代理设置

```bash 
# Enable the go modules feature
export GO111MODULE=on
# Set the GOPROXY environment variable
export GOPROXY=https://goproxy.io

# polipo 代理
export http_proxy=http://127.0.0.1:8123
```