# 修改swap大小

正常ubuntu在新安装系统时，会提示设置swap分区，但是这种方式并不灵活，如果硬盘使用空间较小的ssd，

将本来就不大的空间划分出来一大块，有时候磁盘空间不够用，删除分区很麻烦。

我们可以采用swap文件的方式，在硬盘上创建一个swap文件，在不需要时删除文件即可。

交换分区顾名思义就是在内存不足时与物理内存的数据做交换的，所以最大就设置为物理内存的大小即可，设置太大用不到。

我使用的是ubuntu 18.04，最近用vmware虚拟机装了一个win10，8g内存,2g交换分区，在虚拟机开关机时经常

出现因为内存不够用卡死。



ubuntu18.04默认的swap文件在根目录/下，名字是swapfile

1.查看交换分区大小
free -m 

在创建完毕后也可以用这个命令查看内存情况

2.创建一个swap文件
sudo dd if=/dev/zero of=swap bs=1024 count=8000000

创建的交换文件名是swap，后面的80000000是8g的意思，可以按照自己的需要更改

3.创建swap文件系统
sudo mkswap -f swap

4.开启swap
sudo swapon swap

5.关闭和删除原来的swapfile
sudo swapoff  swapfile

sudo rm /swapfile

6.设置开机启动
sudo vim /etc/fstab

将里面的swapfile改为swap


 ———————————————— 
版权声明：本文为CSDN博主「森森124」的原创文章，遵循CC 4.0 by-sa版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/lhs960124/article/details/80446433