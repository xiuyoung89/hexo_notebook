---
title: Ubuntu+Hexo+Git个人博客搭建笔记总结
date: 2018-12-17 21:17:09
tags:
---

# 写在前边的话

明明可以靠脸吃饭，非要写什么代码，我真的是很羡慕明明。
这个年代，作为一个技术开发人员，如果连个博客都没有，真的很难交到朋友！

## ubuntu环境

Linux wangxy 4.15.0-42-generic #45-Ubuntu SMP Thu Nov 15 19:32:57 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

## node安装

我这里选择是二进制文件安装最新版本，[nodejs官网下载](https://nodejs.org/zh-cn/download/current/)

## hexo安装

```bash
sudo npm install hexo -g
```

## hexo使用生成自己的博客

```bash
makdir myhexo(自己新建的文件夹目录)
hexo init myhexo
cd myhexo
npm install
```

## 先本地部署一篇博客

```bash
hexo new mynewblog
hexo generate
hexo deploy
hexo server
```

在本地现在可以浏览自己新加的博客，现在是把博客部署到github上边

## Hexo部署博客到到github上

### 首先安装 hexo-deployer-git

```bash
  npm install hexo-deployer-git --save
```

github上边新建仓库，如：xiuyoung89.github.io

### 修改配置文件 _config.yml 中最后：

```yml
deploy:
  type: git
  repo: git@github.com:xiuyoung89/xiuyoung89.github.io
  branch: master
```

注：xiuyoung89是github账户名，xiuyoung89.github.io是仓库名

### git-ssh 配置与使用，(参考)

### 重新部署查看

```bash
  hexo clean
  hexo generate
  hexo deploy
```

浏览器访问 xiuyoung89.github.io

完