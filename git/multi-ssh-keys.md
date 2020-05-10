# 配置多个ssh key

> 当使用多个git账户进行开发，如公司项目的gitlab，自己项目的github，并仍使用ssh连接时，需要配置和管理多个ssh key。 

## 生成密钥并配置

- 生成gitlab使用的ssh key，并指定文件名和存储位置（默认~/.ssh/id_rsa）

```Bash
ssh-keygen -t rsa -f ~/.ssh/id_rsa_gitlab -C "useremail"
```

- 生成github使用的ssh key，并指定文件名存储位置

```Bash
ssh-keygen -t rsa -f ~/.ssh/id_rsa_github -C "useremail"
```

- 如果设置过全局用户名和邮箱，取消全局设置

```Bash
git config --global --unset user.name
git conig --global --unset user.email
```

- 在gitlab，github项目下分别设置对应的用户名和邮箱

```Bash
git config user.name [username] 
git config user.email [useremail]
```

- 在~/.ssh/目录下创建config文件，并添加以下内容

```Bash
# gitlab
Host gitlab
    hostName [url]
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_isa_gitlab
# github
Host github 
    hostName github.com 
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_isa_github
```

- 启动ssh-agent，并将生成的ssh key添加到ssh-agent session中

```Bash
ssh-agent Bash
ssh-add ~/.ssh/id_rsa_gitlab
ssh-add ~/.ssh/id_rsa_github
```

- 查看是否添加成功

```Bash
ssh-add -l
```

- 将生成的ssh key分别添加到gitlab，github上

- 测试

```Bash
ssh -T git@github.com
ssh -T git@[gitlab url]
```

## windows下gitBash设置ssh-agent自启动并添加key

> 设置自启动后，每次打开gitBash命令终端，不必再手动启动ssh-agent，手动添加密钥到ssh-agent session中。

- 将以下内容添加到``~/.profile``或``~/.bashrc``文件中

```Bash
env=~/.ssh/agent.env

agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; }

agent_start () {
    (umask 077; ssh-agent >| "$env")
    . "$env" >| /dev/null ; }

agent_load_env

# agent_run_state: 0=agent running w/ key; 1=agent w/o key; 2= agent not running
agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)

if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
    agent_start
    ssh-add ~/.ssh/id_rsa_gitlab
    ssh-add ~/.ssh/id_rsa_github
elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then
    ssh-add ~/.ssh/id_rsa_gitlab
    ssh-add ~/.ssh/id_rsa_github
fi

unset env
```