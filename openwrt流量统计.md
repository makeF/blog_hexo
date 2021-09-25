## 安装bandwidthd
``` shell
opkg update
opkg install bandwidthd #安装

/etc/init.d/bandwidthd enable #开机启动
/etc/init.d/bandwidthd start
```
## 配置
``` shell
vi /etc/config/bandwidthd #配置子网地址
```
**访问地址:** http://`ip`/bandwidthd