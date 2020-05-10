# Win10下安装Yarn和配置

## 安装

> [官网](https://yarnpkg.com/en/docs/install#windows-stable)直接下载安装程序进行安装即可

## 配置 

```Bash
# 查看模块全局安装的位置
yarn global dir

# 查看为安装的可执行文件创建符号链接的位置
yarn global bin

# 设置模块全局安装位置
yarn config set global-folder <path>

# 设置缓存位置
yarn config set cache-folder <path>

# 设置为安装的可执行文件创建符号链接的位置。此项设置完成后，相应地修改用户环境变量的path值
yarn config set prefix <path>
```

> 或者直接编辑~/.yarnrc文件，进行配置