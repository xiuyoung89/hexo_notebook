
# git 仓库完整迁移

```bash
# clone bare 版本
git clone --bare git://github.com/username/project.git

# 把项目推送到远程仓库
git push --mirror git@gitcafe.com/username/newproject.git

# 删除仓库重新更新最新版本

```