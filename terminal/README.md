# Linux

[鳥哥的 Linux 私房菜](http://linux.vbird.org/)

## 基礎指令

* 目錄操作： `ls`, `cd`, `pwd`, `mkdir`, `rmdir`
* 檔案操作： `cp`, `rm`, `mv`
* 檔案內容： `cat [file]`, `more [file]`, `less [file]`

## 目錄

* `/`: 跟目錄
* `~`: home
* `.`: now dir
* `..`: 上一層目錄
* `-`: 上一次的工作目錄

## 快捷鍵

* \[Ctrl\]+\[u\] 清除單行指令
* \[Ctrl\]+\[l\]\`: 清空畫面
* \[shift\]+\[PageUp\], \[shift\]+\[PageDown\]： 上下移動螢幕畫面

## 系統資訊

```text
uname
uname -r # kernel
uname -v # kernel release
uname -m # arch
uname -n # network hostname
uname -a # all info
```

## 語系設定

[https://stackoverflow.com/questions/29609371/how-do-not-pass-locale-through-ssh](https://stackoverflow.com/questions/29609371/how-do-not-pass-locale-through-ssh)

```text
locale # host 語系設定
locale -a # 列出支援的語系

# howto not forward local setting to remote
vim /etc/ssh/ssh_config
# 註解以下設定
# SendEnv LANG LC_*

# 語系測試
LANG="en_IN.utf8" && export LANG
LANG="zh_TW.big5" && export LANG
```

