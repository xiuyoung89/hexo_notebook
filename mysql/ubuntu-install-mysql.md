# ubuntu install mysql

## mysql version选择

1.  apt-get 查看mysql版本

```bash
sudo apt-cache show  mysql-server
#Package: mysql-server
# Architecture: all
# Version: 5.7.21-1ubuntu1
# Priority: optional
# Section: database
# Source: mysql-5.7
# Origin: Ubuntu
# Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
# Original-Maintainer: Debian MySQL Maintainers <pkg-mysql-maint@lists.alioth.debian.org>
# Bugs: https://bugs.launchpad.net/ubuntu/+filebug
# Installed-Size: 162
# Depends: mysql-server-5.7
# Filename: pool/main/m/mysql-5.7/mysql-server_5.7.21-1ubuntu1_all.deb
# Size: 9940
# MD5sum: d04ea92f904b8ab2fb9131c736aa21e2
# SHA1: 981e321230bde35f71e0070284c2339af8b43c59
# SHA256: 35963cb109420749d8e2aa2c9eb1eeae2c2fb8bd68d8eb6d7a49822a4c00f7af
# Homepage: http://dev.mysql.com/
# Description-en: MySQL database server (metapackage depending on the latest version)
#  This is an empty package that depends on the current "best" version of
#  mysql-server (currently mysql-server-5.7), as determined by the MySQL
#  maintainers. Install this package if in doubt about which MySQL
#  version you need. That will install the version recommended by the
#  package maintainers.
#  .
#  MySQL is a fast, stable and true multi-user, multi-threaded SQL database
#  server. SQL (Structured Query Language) is the most popular database query
#  language in the world. The main goals of MySQL are speed, robustness and
#  ease of use.
# Description-md5: b8b44aa3bf1e86bb2834ded6d9d869b5
# Task: lamp-ser
```
自己的要求就是安装mysql5.7版本就可以，所以可以直接用apt-get install 

## 选择 apt-get 在ubuntu 仓库中安装

```bash
apt-get install mysql-client mysql-server mysql-workbench
```

## 第一次使用root权限登陆

```bash
sudo mysql -u root -p
#  直接回车进入
```

## 设置密码

```bash
use mysql;
// 下面这句命令有点长，请注意。
update mysql.user set authentication_string=password('root') where user='root' and Host ='localhost';
update user set plugin="mysql_native_password"; 
flush privileges;
quit;
```