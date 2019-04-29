# 常用操作

## 配置别名

#### 编辑配置.gitconfig文件

```Bash
st = status
ci = commit
co = checkout
br = branch
df = diff
dft = difftool
dfs = diff --staged
dfts = difftool --staged
mr = merge
mrt = mergetool
last = log -1 HEAD
ls = log --oneline --graph --all --decorate
lg = log --oneline --graph --all --decorate --pretty=format:"%h%x20%Cgreen%d%x20%Cred%an%x20%C(yellow)%ad%x20%Creset%s" --full-history --date=short
rb = rebase -i
cp = cherry-pick
```

> 也可使用单条命令：``git config --global alias.co checkout``

## git设置用户名/邮箱

```Bash
# 设置用户名
git config --global user.name [username]

# 设置邮箱
git config --global user.email [useremail]
```

## git代理

```Bash
# 设置代理
git config --global http.proxy
git config --global https.proxy

# 取消设置
git config --global --unset http.proxy
git config --global --unset https.proxy
```

## Git Bash vim中使用粘贴

- 设置为鼠标模式：``:set mouse-=a``
- 鼠标右键粘贴

## 将文件从版本管理中删除

```Bash
git rm --cached -r <dir/file>
git commit -m ""
git push
```

## 远程分支重命名

```Bash
# 删除远程分支
# 方法一
git push origin :branchname
# 方法二
git push orgin --delete branchname

# 重命名本地分支
git branch -m old new

# 提交到远程仓库
git push origin newname
```

## 删除本地分支

```Bash
# 删除
git branch -d branchname

# 强制删除
git branch -D branchname 
```

## 跟踪分支

```Bash
# mber分支跟踪远程分支mdev
git checkout -b mber origin/mdev

# 本地创建一个新分支mdev并跟踪远程分支mdev
git checkout --track origin/mdev 
```

## 查看未合并分支

```Bash
git branch --no-merged
```

## ..

```Bash
# 查看存在于dev但不存在于master中的提交
git log master..dev

# 以下两条命令也可，并可以指定多个引用
git log dev ^master
git log dev not master
```

## ...

```Bash
# 查看分别在master和dev中非两者共有的提交
git log master...dev
```

## 撤销修改

```Bash
# 1.将添加到暂存区的修改撤回到工作区
git reset HEAD <file>

# 2.撤销对工作区文件的修改
git checkout --filename

# 3.修改最近一次的提交内容
git commit --amend

# 4.撤销某次提交
git revert <commit id>
```

## rebase

> 将某一分支上的修改移动到另一分支上。变基会使提交历史看起来很整洁（一条直线，没有分叉）

[参考](https://progit.bootcss.com/#rbdiag_h)

#### 原理

* 找到当前分支和基底分支的共同祖先
* 对比当前分支相对于该祖先的修改，提取修改并存为临时文件
* 将当前分支指向目标基底，然后将保存的临时修改依次应用。

```Bash
# 将dev分支上的修改移动到master分支
git rebase master dev 

# (dev和feature有共同的祖先)选中在feature中但不在dev中的修改，将其重放到master分支上
git rebase --onto master dev feature
```

## stash

```Bash
# 将修改保存为stash条目
git stash push <pathspec>
# git stash 等同于 git stash push 即，将全部修改保存为stash条目

# 从stash列表中弹出一个stash，并应用到当前工作区
git stash pop stash@{id}

# 和pop类似，但不从stash列表中删除 
git stash apply stash@{id}

# 查看所有stash
git stash list

# 将某个stash中的记录内容作为差异(diff)显示 
git stash show stash@{id}
git stash show -p stash@{id}

# 删除特定stash
git stash drop stash@{id}

# 清除所有stash
git stash clear

# 创建stash分支
git stash branch <name>
```

## patch

```Bash
git format-patch [commit id] [commit id]
git format-patch [commit id] -n

# 某次提交后的所有patch
git format-patch [commit id]
```

## git在某个提交处检出分支

```Bash
git log
git checkout commitID -b branch_name
```

## 查看差异

```Bash
# 查看本地工作区修改与暂存区文件内容差异
git diff

# 提交到暂存区，未提交到仓库的修改
git diff --cached 

# 直接和某次提交进行比较
git diff commitID
```

## 快速合并(fast forward)

> 当前分支所有的提交已包含在另一个分支中，则对当前分支执行快速合并，不会产生新的提交，只将当前分支指向合并进来的分支。

## 忽略指定文件

- 在.gitignore中添加要忽略的文件
- 如果要忽略的文件已经在版本管理中，需要将其在缓存中删除
    - ``git rm -r --cached [file name]``