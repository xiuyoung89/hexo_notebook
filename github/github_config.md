---
title: github代理配置
date: 2019-02-18 17:30:00
tags:
---

# github代理配置

```bash
git config --global http.proxy 'socks5://127.0.0.1:1080'
git config --global https.proxy 'socks5://127.0.0.1:1080'
```

# 取消代理配置

```bash
git config --global unset uhttp.proxy
git config --global unset https.proxy
```