## 知识点
> 流量路径: xray 'inbound -> port'配置设置监控端口,可配置xtls,由xray分辨流量类型,xray流量走代理,其他流量回落到'fallbacks'设置的端口服务  
 
## 安装xray
提前安装`curl unzip`  
`bash -c "$(curl -L https://github.com/XTLS/Xray-install/raw/main/install-release.sh)"`  
[官方脚本地址](https://github.com/XTLS/Xray-install)  

## 配置xray
[官方配置文件示例](https://github.com/XTLS/Xray-examples)  
[官方配置文档](https://xtls.github.io/config/)  
推荐'vless-tcp-xtls'  

[tls证书申请](/index.php/archives/11/)
## 配置客户端
![](https://cdn.jsdelivr.net/gh/makeF/images@master/host/20210411025428.jpg)  
> 免流的混淆,在v2rayNG就是域名伪装  
> 域名伪装可以包含端口,[domain:port] [常用免流域名](https://www.xg6.cn/thread-1909-1-1.html)  
> 路径"/",应该可以不要  
## 调试
在'log'下修改配置:  
``` json
"access": "/var/log/v2ray/access.log",
"error": "/var/log/v2ray/error.log",
"loglevel": "debug"
```
重启xray,查看日志  
``` shell
systemctl restart xray

#持续输出日志
tail -f /var/log/v2ray/access.log
```
