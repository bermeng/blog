# Ubuntu下软件安装

## redis 安装

```Bash
# 源码下载
wget http://download.redis.io/releases/redis-4.0.10.tar.gz
# 解压
tar -xzf redis-4.0.10.tar.gz
# 编译（若无gcc，需安装：``apt install gcc``）
make
# 安装
make install
# 配置
redis.conf
# 启动
redis-server ./redis-4.0.10/redis.conf
# redis客户端
redis-cli
```

## 手动golang安装

```Bash
# 官网下载源码包
# 解压
# 配置环境变量：~/.bashrc文件末尾追加
export GOROOT=/usr/local/go
export GOPATH=/mnt/d/GoWork
export PATH=$PATH:$GOROOT/bin
```

## mysql安装

```Bash
# 安装（安装过程中会让输入密码）
apt install mysql-server
apt install mysql-client
# 配置文件
/etc/mysql/mysql.conf.d/mysqld.cnf
# 启动
service mysql start
# 登录
mysql -u root -p
# 远程访问授权
grant all privileges on *.* to 'username'@'%' identified by 'passwd'; flush privileges;
```

## Ubuntu下解决make没有安装

```Bash
apt install build-essential
```

## 更新git

```Bash
add apt-get-repository ppa:git-core/ppa
apt-get update
apt-get install git
```