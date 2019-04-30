# Ubuntu 常用命令

1. 查看磁盘空间
   df -lh
   du -lh --max-depth=1 
   du -bsh /usr             // 查看单个文件夹大小

2. 查看程序异常关闭的原因
   2.1 内存溢出导致的异常关闭： dmesg | egrep -i -B100 ‘killed process’ 

3. 命令行临时代理设置
   ```bash
    export https_proxy="socks5://127.0.0.1:1080"
    export http_proxy="socks5://127.0.0.1:1080"
   ``` 
4. 清理登陆信息
   
   ```bash
    echo > /var/log/wtmp
    echo > /var/log/btmp
    echo > /var/log/lastlog
    history -c
   ```
5.  nvidia 显卡安装
    方法一：直接apt-get 安装
    ```bash
    sudo add-apt-repository ppa:graphics-drivers/ppa
    sudo apt-get update

    sudo ubuntu-drivers devices
    # == /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
    # modalias : pci:v000010DEd00001F08sv00007377sd00001501bc03sc00i00
    # vendor   : NVIDIA Corporation
    # driver   : nvidia-driver-418 - third-party free
    # driver   : nvidia-driver-415 - third-party free
    # driver   : nvidia-driver-430 - third-party free recommended
    # driver   : xserver-xorg-video-nouveau - distro free builtin

    sudo ubuntu-drivers autoinstall         # restart 
    ```
