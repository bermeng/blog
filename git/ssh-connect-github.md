# SSH连接GitHub

1. ``ssh-keygen -t rsa -C email地址``
2. 复制上一步生成的文件id_rsa.pub的内容
3. 进入github账号设置中，new ssh key 将上一步复制的内容粘贴进去
4. 测试：``ssh -T git@github.com``

## 设置SSH后push仍需要输入密码问题解决

> 原因：clone仓库时使用的https方式

### 解决：修改origin

- 方法一

``git remote set-url [url]``

- 方法二 

```text
git rm origin
git add remote orgin [url]
```
    
- 方法三

``直接修改.git/config文件中的url``