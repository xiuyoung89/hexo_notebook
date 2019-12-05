<!--
 * @title: Do not edit
 * @date: YYYY-MM-DD HH:mm:ss
 * @author: Young
 -->
## goland 编译windows程序

```bash
env CGO_ENABLED=1 GOOS=windows GOARCH=amd64 CC=x86_64-w64-mingw32-gcc go build -o analyaer-server ./src/main.go
```