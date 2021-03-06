# Basis

## 文件时间

- mtime：文件内容更改时，更新该时间。
- ctime：文件属性更改时，更新该时间，如文件属性或权限。
- atime：读取文件内容时，更新该时间。
- 通过 touch 命令可修改文件日期，时间。

## umask

> 用于指定用户创建文件或目录时的权限默认值

- 新建文件权限：666 去掉 umask 权限
- 新建目录权限：777 去掉 umask 权限

## 文件隐藏属性

- `chattr`：设置文件隐藏属性。常用参数：`a`，`i`。
- `lsattr`：显示文件隐藏属性。

> **该命令需在 ext2/ext3 文件系统上使用**

## 文件特殊权限

- SUID（4）：针对文件，在文件所有者可执行权限位置
- SGID（2）：针对文件或目录，在文件用户组可执行权限位置
- SBIT（1）：针对目录，在 others 可执行权限位置

## 文件查找

- 一般首先考虑使用`whereis`，`locate`命令查找（基于数据库查找，速度快）
- 最后考虑使用`find`查找（查找硬盘，较慢）

### locate

> `locate`根据`/var/lib/mlocate/mlocate.db`数据库进行查找。新建的文件需执行`updaedb`后才能被查到。

### updatedb

> `updatedb`根据`/etc/updatedb.conf`的设置查找系统硬盘内的文件名，并更新`/var/lib/mlocate/mlocate.db`内的数据文件。

### find

> `find / -perm +7000 -exec ls -l {} \;`

- `{}`代表 find 查找的内容
- `-exec`代表额外命令的开始
- `\;`代表额外命令的结束
- `ls -l {}`代表额外命令

### which

> 查找可执行程序所在位置

## 其他

- `basename`：获取文件名
- `dirname`：获取目录名
- `cp`：`-a`相当于`pdr`参数组合
  - `p`：连同文件属性一起复制
  - `d`：若源文件是链接文件，则复制链接属性
  - `r`：递归
- `cat`：`-A`相当于-vET 参数组合
  - `v`：列出一些特殊字符
  - `E`：将结尾断行符\$显示出来
  - `T`：将 Tab 键以^I 显示出来
- `head`

```text
# 列出100行之前的行
head -n -100 /etc/man.config
# 列出100行之后的行
tail -n +100 /etc/man.config
```

- `pgrep -l ${name}`显示进程名和 PID
- `&`：后台运行
- `nohup`：不挂起；exit 退出当前账户后，进程仍继续运行
- `2>&1`：将标准出错重定向到标准输出
