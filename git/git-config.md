# Git 設定

所有設定會記錄在 `home` 目錄下的 `.gitconfig`

如果 project 需要自訂的話，請在該目錄下新增 `.gitconfig`

## 設定方式 － 透過指令

```bash
# 查看設定
git config --list # git config -l
less ~/.gitconfig

# username & email
git config --global user.name "username"
git config --global user.email "username@example.com.tw"

# core
git config --global core.editor vim
git config --global core.ignoreCase false

# push Git 2.0 開始已為預設
git config --global push.default simple

# console 上顏色
git config --global color.diff auto
git config --global color.status auto
git config --global color.branch auto
git config --global color.log auto
```

## 設定方式 － 編輯檔案

用你習慣用編輯器來開啟 `home` 目錄下的 `.gitconfig` 編輯吧

```text
[user]
        name = username
        email = username@example.com.tw
[core]
        editor = vim
        ignorecase = false
[push]
        default = simple
[color]
        diff = auto
        status = auto
        branch = auto
        log = auto
[alias]
        lg = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cblueby %an %Cgreen(%cr)%Creset'
```

## 別名設定（alias）

git 指令打久了，每次都要打很多字覺得很煩時可以設定別名喔

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.aa add --all
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.lg "lg = log --graph --pretty=format:'%C(reverse ul cyan)%h%Creset -%C(yellow)%d%Creset %C(ul)%s%Creset %C(dim white)<%an>%Creset %Cgreen(%cr)%Creset %ci'"
```

## Gitignore

不要新增到歷史紀錄的檔案，參考[範例](https://github.com/github/gitignore)

```bash
curl https://api.github.com/gitignore/templates

curl https://api.github.com/gitignore/templates/Composer
curl https://api.github.com/gitignore/templates/Laravel

curl https://api.github.com/gitignore/templates/Java
curl https://api.github.com/gitignore/templates/Gradle
curl https://api.github.com/gitignore/templates/Maven

curl https://api.github.com/gitignore/templates/Node
```

## Gitkeep

保留空資料夾，如上傳圖片的路徑

```bash
cd img
touch .gitkeep
```

