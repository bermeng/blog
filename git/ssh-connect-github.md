# SSH连接GitHub

1. ``ssh-keygen -t rsa -C email地址``
2. 复制上一步生成的文件id_rsa.pub的内容
3. 进入github账号设置中，new ssh key 将上一步复制的内容粘贴进去
4. 测试：``ssh -T git@github.com``