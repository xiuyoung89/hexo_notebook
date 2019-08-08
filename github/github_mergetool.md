# github mergetool


## vim config

vim .gitconfig

1. use p4merge
```bash
[http]
  proxy = socks5://127.0.0.1:1080
[https]
  proxy = socks5://127.0.0.1:1080
[user]
  email = xiuyoung89@163.com
  name = young

[merge]
        keepBackup = false
        tool = p4merge
[mergetool]
        prompt = false
[mergetool "p4merge"]
        cmd = p4merge "$BASE" "$LOCAL" "$REMOTE" "$MERGED"
        keepTemporaries = false
        trustExitCode = false
        keepBackup = false
[diff]
        tool = p4merge
[difftool]
        prompt = false
[difftool "p4merge"]
        cmd = p4merge "$LOCAL" "$REMOTE"
        keepTemporaries = false
        trustExitCode = false
        keepBackup = false
```

2. add beyond compare

```bash
[diff]
  tool = bcomp
[difftool]
  prompt = false
[difftool "bcomp"]
  trustExitCode = true
  cmd = "/usr/bin/bcompare" \"$LOCAL\" \"$REMOTE\"
[merge]
  tool = bcomp
[mergetool]
  prompt = false
[mergetool "bcomp"]
  trustExitCode = true
  cmd = "/usr/bin/bcompare" \"$LOCAL\" \"$REMOTE\" \"$BASE\" \"$MERGED\"
```