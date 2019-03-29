# ubuntu下软件安装

## redis 安装

1. 源码下载：``wget http://download.redis.io/releases/redis-4.0.10.tar.gz``
2. 解压：``tar -xzf redis-4.0.10.tar.gz``
3. ``make``（若无gcc，需安装：``apt install gcc``）
4. ``make install``
5. 配置``redis.conf``文件
6. 启动：``redis-server ./redis-4.0.10/redis.conf``
7. redis客户端：``redis-cli``

## 手动golang安装

1. 官网下载源码包
2. 解压
3. 配置环境变量：``~/.bashrc``文件末尾追加
    - ``export GOROOT=/usr/local/go``
    - ``export GOPATH=/mnt/d/GoWork``
    - ``export PATH=$PATH:$GOROOT/bin``

## mysql安装

1. ``apt install mysql-server``（安装过程中会让输入密码）
2. ``apt install mysql-client``
3. 配置文件：``/etc/mysql/mysql.conf.d/mysqld.cnf``
4. 启动：``service mysql start``
5. 登录：``mysql -u root -p``
6. 远程访问授权：``grant all privileges on *.* to 'username'@'%' identified by 'passwd'; flush privileges;``

## Ubuntu下解决make没有安装

> ``$ apt install build-essential``

## 更新git

```shell
$ add apt-get-repository ppa:git-core/ppa
$ apt-get update
$ apt-get install git
```