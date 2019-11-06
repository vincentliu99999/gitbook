# Git 遠端操作

## Github 設定

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
less ~/.ssh/id_rsa.pub
```

[Github - SSH Keys](https://github.com/settings/keys) &gt; New SSH key

```bash
git add remote.md
git commit -m "remote test"
git push -u

# 新增遠端repository
git remote add remote_branch git@github.com:remote_branch/repository.git

# 檢視遠端repository
git remote
git remote -v
git remote show origin

# 移除遠端repository
git remote rm remote_branch

# 切換到遠端分支
git checkout --track origin/remote_branch
```

