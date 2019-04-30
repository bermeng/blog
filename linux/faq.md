# FAQ

## centos下安装jdk


```Bash
# 查找centos中是否已安装有默认的openjdk
$ rpm -qa | grep java

# 卸载openjdk
$ yum -y remove [openjdk]
# 或者
$ rpm -e --nodeps [openjdk]

# 安装
$ yum install [jdk rpm包]

# 安装完成后创建链接
$ cd /usr/bin
$ ln -s /usr/java/jdk1.7.0/bin/java java

# 配置环境变量：
export JAVA_HOME=/usr/java/jdk1.7.0_55  
export JRE_HOME=$JAVA_HOME/jre  
export PATH=$PATH:$JAVA_HOME/bin  
export CLASSPATH=./:$JAVA_HOME/lib:$JRE_HOME/lib 

# 配置完成后，检测是否成功
$ java -version

# 若出现报错-bash: /usr/bin/java: /lib/ld-linux.so.2: bad ELF interpreter: 没有那个文件或目录
$ sudo yum install glibc.i686
```

## 设置ip配置永久生效  

```Bash
$ vi /etc/sysconfig/network-scripts/ifcfg-eth0
# 将onboot设置为yes即可。
```

## 为普通用户赋予sudo权限

1. 打开``/etc/sudoers``文件
2. 在``root ALL=(ALL) ALL``这一行下面添加：``user ALL=(ALL) ALL``。

## centos误删root用户家目录

```Bash
# 创建root目录
$ mkdir /root
# 复制/etc/skel/下的隐藏文件到/root目录下
$ cp /etc/skel/.bash* /root
# 重启
$ reboot
```

## centos6.5安装mysql

```Bash
# 下载
$ wget https://dev.mysql.com/get/https://dev.mysql.com/get/

# 安装下载的rpm文件
$ yum install mysql-community-release-el6-5.noarch.rpm 

# 查看可安装源
$ yum repolist enabled | grep mysql

# 在/etc/yum.repos.d/mysql-community.repo文件中可设置安装源

# 使用yum安装mysql
$ yum install mysql-server

# 启动mysql服务
$ service mysqld start

# 设置开机启动
chkconfig mysqld on

# 设置字符集为UTF-8
$ vim /etc/my.cnf
# 在[mysqld]部分添加：character-set-server=utf8
在文件末尾新增[client]段，并在[client]段添加：default-character-set=utf8

# 重启服务
$ service mysql restart
```

## centos本地安装mysql  

```Bash
# 将mysql的rpm包上传到centos执行以下命令

$ rpm -ivh mysql-community-common-5.7.16-1.el6.x86_64.rpm
$ rpm -ivh mysql-community-libs-5.7.16-1.el6.x86_64.rpm
$ rpm -ivh mysql-community-client-5.7.16-1.el6.x86_64.rpm
$ rpm -ivh mysql-community-server-5.7.16-1.el6.x86_64.rpm
```

> 参数说明：i：install；v:verbose进度条；h:hash校验

> 安装过程中会出现包依赖问题，通过yum安装相应包解决即可。

#### 注意
> MySQL5.7.4之前的版本默认没有密码。之后的版本可通过``grep 'temporary password' /var/log/mysqld.log``命令找到初始密码，进行登录并修改密码。