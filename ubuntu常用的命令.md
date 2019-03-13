# Ubuntu 常用命令

1. 查看磁盘空间
   df -lh
   du -lh --max-depth=1 
   du -bsh /usr             // 查看单个文件夹大小

2. 查看程序异常关闭的原因
   2.1 内存溢出导致的异常关闭： dmesg | egrep -i -B100 ‘killed process’ 