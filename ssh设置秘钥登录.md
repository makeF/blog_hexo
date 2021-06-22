## 设置秘钥

### 生成秘钥

``` bash
ssh-keygen

#Enter passphrase (empty for no passphrase): <== 输入密钥锁码，或直接按 Enter 留空
#Enter same passphrase again: <== 再输入一遍密钥锁码
#密码锁可以保护私钥不被盗用
```
### 上传秘钥
``` bash
cat id_rsa.pub >> ~/.ssh/authorized_keys
```

### 设置配置文件

``` bash
vim /etc/ssh/sshd_config

#修改配置
PubkeyAuthentication yes
#RSAAuthentication yes
#PermitRootLogin yes #允许root用户登录
#PasswordAuthentication no #禁用密码登录

#重启sshd服务
systemctl reload sshd
```

## 问题
 - 配置好公钥登录依然要输入密码
 > 查看日志文件  
 > `tail -n 20 /var/log/auth.log`  

 > 修改文件夹权限   
 > `chmod 700 ~/.ssh、authorized_keys`  
 > `chmod 600 ~/.ssh、`  
