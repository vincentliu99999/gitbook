# Git 基礎

工作環境

1. Workspace: 開發中的工作目錄
2. Staging Area: 暫存區
3. Repository: 儲存庫
4. Remote: 遠端

手足無措時，先深呼吸，再下指令 `git status`

## 建立專案

```bash
# way1: 建立名為 project-name 的 Repository
mkdir [project-name]
git init

# way2: 建立名為 project-name 的 Repository
git init [project-name]

# 下載 Repository
git clone [url]
```

## 檔案管理－新增、刪除、修改

```bash
# 新增到暫存區：指定檔案名稱
git add [file1] [file2]

# 新增到暫存區：搜有動過的檔案
git add .

# 新增空目錄
mkdir [dir]
cd [dir]
touch .gitkeep

# 清除檔案
git clean -f

# 清除目錄
git clean -df

# 暫存區移除檔案
git rm --cached [file1] [file2]
```

## 提交變更記錄

```bash
# 提交到儲存庫
git commit -m [message]

# 修改最後一次提交的訊息
git commit --amend

# 合併最後一次提交的訊息
git commit --amend -m [message]
```

## 查看紀錄

```bash
git log

# 精簡版
git log --graph --oneline

# 單一檔案的紀錄
git log -p [file]

# 每一行檔案的紀錄
git blame [file]

# 顯示所有提交更動的內容
git show [object]
```

