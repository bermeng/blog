# 常用操作

## 配置别名

### 编辑配置.gitconfig文件

```text
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

- 也可使用单条命令：``git config --global alias.co checkout``

## git设置用户名/邮箱

- ``git config --global user.name [username]``
- ``git config --global user.email [useremail]``

## git设置和取消代理

- ``git config --global http.proxy``
- ``git config --global https.proxy``
- ``git config --global --unset http.proxy``
- ``git config --global --unset https.proxy``

## git bash vim中使用粘贴

- 设置为鼠标模式：``:set mouse-=a``
- 鼠标右键粘贴

## git 文件不提交到远程仓库，但本地不删除

- ``git rm --cached -r somedir(file)``
- ``git commit -m ""``
- ``git push``

## 远程分支重命名

- 删除远程分支：``git push origin :branchname``（或者：``git push orgin --delete branchname``）
- 重命名本地分支：``git branch -m old new``
- 提交到远程仓库：``git push origin newname``

## 删除本地分支

- ``git branch -d branchname``

## 跟踪分支

- ``git checkout -b mber origin/mdev //mber分支跟踪远程分支mdev``
- ``git checkout --track origin/mdev //本地创建一个新分支mdev并跟踪远程分支mdev``

## 查看尚未合并的分支

- ``git branch --no-merged``

## 撤销修改

- ``git reset HEAD <file> //将添加到暂存区的修改撤回到工作区``
- ``git checkout --filename //将工作区的修改撤销``
- ``git commit --amend //修改最近一次的提交内容``

## rebase

- ``git rebase --onto master server client``

## stash

- ``git stash``
- ``git stash apply``
- ``git stash pop``
- ``git stash list``
- ``git stash show -p``
- ``git stash show stash@{id}``
- ``git stash drop``
- ``git stash branch [name]`` //创建stash分支

## patch

- ``git format-patch [commit id] [commit id]``
- ``git format-patch [commit id] -n``
- ``git format-patch [commit id``] //某次提交后的所有patch

## git在某个提交处检出分支

```text
git log
git checkout commitID -b branch_name
```

## 查看差异

- ``git diff //查看本地工作区修改与暂存区文件内容差别``
- ``git diff --cached //提交到暂存区，未提交到仓库的修改``
- ``git diff commitID //直接和某次提交进行比较``

## 快速合并(fast forward)

> 当前分支所有的提交已包含在另一个分支中，则对当前分支执行快速合并，不会产生新的提交，只将当前分支指向合并进来的分支。

## 忽略指定文件

- 在.gitignore中添加要忽略的文件
- 如果要忽略的文件已经在版本管理中，需要将其在缓存中删除
    - ``git rm -r --cached [file name]``