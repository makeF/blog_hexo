## 安装软件
``` shell
apt install nginx php php7.3-fpm
```
## 默认配置
文件位置:`/etc/nginx/sites-enabled/default`  
``` nginx
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        root /var/www/html;
        index index.html index.php index.htm index.nginx-debian.html;
        server_name _;

        location / {
                try_files $uri $uri/ =404;
        }

        # pass PHP scripts to FastCGI server
        #
        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
        #使用 unix(php-fpm) or tcp(php-cgi)
                fastcgi_pass unix:/run/php/php7.3-fpm.sock;
        #       fastcgi_pass 127.0.0.1:9000;
        }
}
```