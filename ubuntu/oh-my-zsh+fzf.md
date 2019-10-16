---
    title: ubuntu install oh-my-zsh  +  fzf
    date:  2019-10-16
    comments: hugo
---

# ubuntu install oh-my-zsh  +  fzf

1. install zsh

```bash
# 安装 Zsh
sudo apt-get install zsh

# 将 Zsh 设置为默认 Shell
chsh -s /bin/zsh

# 可以通过 echo $SHELL 查看当前默认的 Shell，如果没有改为 /bin/zsh，那么需要重启 Shell。
```

2. install on-my-zsh

```bash
# 安装 Oh My Zsh
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh
```

3. 配置oh-my-zsh

```bash
vim .zshrc
#plugins=(
# 	        git 
#        	golang 
# 	        zsh-syntax-highlighting 
# 	        zsh-autosuggestions
# )
```