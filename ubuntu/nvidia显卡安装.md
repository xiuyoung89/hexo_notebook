# nvidia 显卡安装

1. 卸载低版本的英伟达驱动

```bash
sudo apt-get purge nvidia*
```

2. 把显卡驱动加入PPA

```bash
sudo add-apt-repository ppa:graphics-drivers
sudo apt-get update
```

3. 查找英伟达显卡驱动最新版本号

```bash
sudo apt-cache search nvidia
```

4. 查看系统推荐版本

```bash
ubuntu-drivers devices

# == /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
# modalias : pci:v000010DEd00001F08sv00007377sd0000150Abc03sc00i00
# vendor   : NVIDIA Corporation
# driver   : nvidia-driver-435 - third-party free recommended
# driver   : nvidia-driver-415 - third-party free
# driver   : nvidia-driver-430 - third-party free
# driver   : xserver-xorg-video-nouveau - distro free builtin
```

5. 安装推荐版本

```bash
sudo apt-get install nvidia-driver-435
```