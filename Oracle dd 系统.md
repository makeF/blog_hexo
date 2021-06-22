## 新建实例
创建新实例,并选择镜像为 Ubuntu 16.04  
![20210123135639](https://cdn.jsdelivr.net/gh/makeF/images/host/20210123135639.png)  

高级选项 -> 管理 -> 粘贴init脚本  
![20210123135831](https://cdn.jsdelivr.net/gh/makeF/images/host/20210123135831.png)  
**默认密码 root:Abc123456**
``` shell
#!/bin/bash
echo root:Abc123456 |sudo chpasswd root
sudo sed -i 's/^#\?PermitRootLogin.*/PermitRootLogin yes/g' /etc/ssh/sshd_config;
sudo sed -i 's/^#\?PasswordAuthentication.*/PasswordAuthentication yes/g' /etc/ssh/sshd_config;
sudo service sshd restart
```
## dd系统
debian 10 64bit (推荐，来回dd几十次正常):
``` shell
bash <(wget --no-check-certificate -qO- 'https://moeclub.org/attachment/LinuxShell/InstallNET.sh') -d 10 -v 64 -a -firmware
```
Ubuntu 16.04 64bit (不推荐):
``` shell
bash <(wget --no-check-certificate -qO- 'https://moeclub.org/attachment/LinuxShell/InstallNET.sh') -u 16.04 -v 64 -a -firmware
```

**dd时间大概15分钟左右 初始账号: root 密码: MoeClub.org**  
**换密码: `passwd`**  

## bbr加速
`https://github.com/ylx2016/Linux-NetSpeed`  

## 安装软件
``` shell
wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/mack-a/v2ray-agent/master/install.sh" && chmod 700 /root/install.sh && /root/install.sh
```
**选择2,单独安装所选项**  
![20210123151728](https://cdn.jsdelivr.net/gh/makeF/images/host/20210123151728.png)  
## 修改DNS
``` shell
apt-get install resolvconf
vim /etc/resolvconf/resolv.conf.d/head

#修改内容
nameserver 1.1.1.1
nameserver 8.8.8.8
```