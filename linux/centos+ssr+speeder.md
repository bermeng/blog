# centos下ssr搭建并配置锐速

## 锐速安装

```shell
# 查看自己vps内核版本
$ uname -r

# 查看91yun支持锐速的内核版本库中是否有自己vps的内核版本号
# 若内核不支持，修改内核，即下载支持的内核版本
$ rpm -ivh [kernel URL] --force

# 下载锐速脚本进行安装
$ wget -N --no-check-certificate https://raw.githubusercontent.com/91yun/serverspeeder/master/serverspeeder-all.sh && bash serverspeeder-all.sh

# 卸载命令
$ chattr -i /serverspeeder/etc/apx* && /serverspeeder/bin/serverSpeeder.sh uninstall -f
```

## ssr安装

```shell
# 下载ssr安装脚本：teddysun或doubi
$ wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh
chmod +x shadowsocks.sh
$ bash shadowsocks.sh

# 按照操作步骤进行即可
```