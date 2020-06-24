
##  git 仓库完整迁移

```bash
# clone bare 版本
git clone --bare git://github.com/username/project.git

# 把项目推送到远程仓库
git push --mirror git@gitcafe.com/username/newproject.git

# 删除仓库重新更新最新版本

```


## 或者别的方式

```bash
1.先克隆老项目的镜像

git clone --mirror old.git (old.git 为老项目的git地址)

2.进入老项目的目录

cd old.git

3.移除老项目的地址替换成新项目

git remote set-url --push origin  new.git (new.git 为新项目的git地址)

4.将镜像推到远程

git push --mirror  //这一步需要输入新的git的账号和密码
四步就搞定了。
```