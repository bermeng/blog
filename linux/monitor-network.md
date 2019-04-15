# 网络流量监控工具

## iptraf

```Bash
# 安装
yum -y install iptraf

# 启动
iptraf-ng
```

## SAR

```Bash
# 安装
yum -y install sysstat

# 使用 

sar -n { DEV | EDEV | NFS | NFSD | SOCK | ALL }
```

## iftop

```Bash
# 没有可用的yum源，所以手动编译安装

# 安装依赖
 yum install -y byacc libpcap ncurses-devel libpcap-devel

# 下载iftop
wget http://www.ex-parrot.com/pdw/iftop/download/iftop-1.0pre4.tar.gz

# 解压
tar -xzf iftop-1.0pre4.tar.gz

# 进入到iftop-1.0pre4.tar.gz目录
cd iftop-1.0pre4.tar.gz

# 配置
./configure

# 编译并安装
make && make install
```