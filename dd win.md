## 选择合适的dd包
> 来自 d.nat.ee  
> [win7 sp1](http://d.nat.ee/win/lite/win7-ent-sp1-x64-cn/win7-ent-sp1-x64-cn.vhd.gz)  
> [server 2012](http://d.nat.ee/win/lite/winsrv2012r2-data-x64-cn/winsrv2012r2-data-x64-cn.vhd.gz)  
> 用户名：Administrator 密码：nat.ee  
> [efi.vhd.gz](http://d.nat.ee/win/lite/winsrv2012r2-data-x64-cn/winsrv2012r2-data-x64-cn-efi.vhd.gz) 仅适用支持uefi启动启动, 如甲骨文  

## 安装运行库
``` shell
apt-get update
apt-get install -y xz-utils openssl gawk file
```
## 一键脚本
``` shell
wget --no-check-certificate -qO InstallNET.sh 'http://d.nat.ee/sh/InstallNET.sh' && bash InstallNET.sh -dd 'dd包地址'
```

## 启动widows
等待 vps dd 完成后,进入vnc,发现卡在`grub`界面,按`c`输入`exit`退出后,自动进入windows启动界面.  
进入系统后,打开`cmd`输入`mkdir C:\Boot\grub2 && echo chainloader +1  >> C:\Boot\grub2\grub.cfg && echo boot  >> C:\Boot\grub2\grub.cfg`防止重启后卡`grub`

## 其他设置
进入系统自行到网络设置配置ip  
激活系统: 
``` cmd
slmgr /skms kms.moerats.com
slmgr /ato
```
或者[下载脚本](https://www.moerats.com/kms/)  
