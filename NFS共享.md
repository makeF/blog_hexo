## 外网机安装NFS服务端
``` shell
apt-get install nfs-kernel-server
```
## 创建共享目录机配置参数
``` shell
#修改黑名单 /etc/hosts.deny
rpcbind mountd nfsd statd lockd rquotad : ALL                      #阻断所有

#修改白名单 /etc/hosts.allow, domain为客户机域名或IP
rpcbind mountd nfsd statd lockd rquotad : 127.0.0.1 : allow        #允许本地
rpcbind mountd nfsd statd lockd rquotad : domain : allow       #允许客户机
rpcbind mountd nfsd statd lockd rquotad : ALL : deny               #阻断其他

#设置共享目录
mkdir /var/nfs                          #创建文件夹
chown nobody:nogroup /var/nfs           #设置用户
chmod 755 /var/nfs                      #设置权限

#编辑/etc/exports, 允许客户机访问共享目录
/var/nfs domain(rw,sync,no_subtree_check)

#重启客户端
service nfs-kernel-server restart
```

## 客户端配置
``` shell
#安装客户端
apt-get install nfs-common

#设置共享目录
mkdir /root/nfss

#挂载服务器共享目录, server_IP:服务器IP
mount server_IP:/var/nfs /root/nfss

#检查是否挂载成功
df -h
```