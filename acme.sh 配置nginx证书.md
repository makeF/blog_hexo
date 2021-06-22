## 安装 acme.sh  
```bash
 curl  https://get.acme.sh | sh
 ```  
## nginx生成证书
```bash
acme.sh --issue  -d mydomain.com  --nginx
```  
## 复制证书
> 先创建文件夹  
> `mkdir /etc/nginx/conf.d/example`
```bash
acme.sh --install-cert -d example.com \
--key-file       /etc/nginx/conf.d/example/key.pem  \
--fullchain-file /etc/nginx/conf.d/example/cert.pem \
--reloadcmd     "service nginx force-reload"
```  
## nginx ssl配置
```bash
server {
    listen 443;
    #域名
    server_name example.com;
    ssl on;
    #根目录
    root /var/www/example.com; 
    index index.html index.htm;
    #证书秘钥
    ssl_certificate  /etc/nginx/conf.d/example/cert.pem;
    ssl_certificate_key /etc/nginx/conf.d/example/key.pem;
    
    ssl_session_timeout 5m;
    ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    ssl_prefer_server_ciphers on;
    location / {
        index index.html index.htm;
    }
}
server {
    listen 80;
    # 域名
    server_name example.com;
    # 把http的域名请求转成https
    rewrite ^(.*)$ https://$host$1 permanent;
}
```  