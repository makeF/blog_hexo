优缺点:  
* 免费不限速不限量  
* 标准web端口  
* 美国服务器延迟略高
----
## 准备
域名  
cloudflare账号  
域名接入cloudflare  
## 安装使用
下载[cloudflared](https://github.com/cloudflare/cloudflared/releases)  
``` shell
# 登录
cloudflared tunnel login #自动打开浏览器
# 运行
cloudflared tunnel --hostname <tunnelDomain> --url localhost:[端口] #tunnelDomain需要未手动解析
```