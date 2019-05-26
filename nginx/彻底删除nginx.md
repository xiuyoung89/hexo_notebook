

# ubuntu18.04彻底删除nginx

```bash
    sudo apt-get --purge remove nginx 
    sudo apt-get autoremove 
    dpkg --get-selections|grep nginx 

    # 罗列出与nginx相关的软件
    nginx-common deinstall 

    # 然后
    sudo apt-get --purge remove nginx-common 
    sudo apt-get install nginx 
```

