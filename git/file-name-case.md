# git修改文件名大小写

> git默认忽略文件名的大小写

- 方法一

```Bash
# 修改文件名
$ git mv FAQ.md faq.md

# 本地提交
$ git commit -m "rename"

# push到远程仓库
$ git push
```

- 方法二

```Bash
# 设置git大小写敏感
$ git config core.ignorecase false

# 修改文件名
$ mv FAQ.md faq.md

# 缓存中删除FAQ.md文件(若不进行此操作，提交到远程仓库后，会同时存在FAQ.md和faq.md文件)
$ git rm -r --cached FAQ.md

# 添加缓存
$ git add -A

# 本地提交
$ git commit -m "rename"

# push到远程仓库
$ git push
```
