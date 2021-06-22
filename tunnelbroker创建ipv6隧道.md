## 创建隧道
### 注册tunnelbroker账号
[注册](https://tunnelbroker.net)  
### 创建隧道
[创建隧道](https://tunnelbroker.net/new_tunnel.php)  
![20210318002459](https://cdn.jsdelivr.net/gh/makeF/images/host/20210318002459.png)
输入服务器ipv4地址,确保ipv4能ping通  
选择隧道服务器,一般选择洛杉矶延迟较低  

## 配置隧道
### 修改vps配置
``` shell
vim /etc/sysctl.conf

# 添加配置
net.ipv6.conf.all.disable_ipv6 = 0
net.ipv6.conf.default.disable_ipv6 = 0
net.ipv6.conf.lo.disable_ipv6 = 0

# 使设置生效
sysctl -p
```  
### 添加ipv6配置
![20210318003449](https://cdn.jsdelivr.net/gh/makeF/images/host/20210318003449.png)  

把HE给出的命令复制到`/etc/network/interfaces`  
**local_ip设置为公网ip或内网ip**

### 添加 ipv6 dns
* google: 2001:4860:4860::8888  
* baidu: 2400:da00::6666  
* ali: 2400:3200::1
* 或者 HE `DNS Resolvers`所提供的  

## 测试联通
ping不通重启
`ping 2400:3200::1`