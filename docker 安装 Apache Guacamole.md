## 拉取Guacamole服务器、Guacamole客户端和MySQL的Docker镜像
``` shell
docker pull guacamole/guacamole
docker pull guacamole/guacd
docker pull mysql/mysql-server
```

## 运行Mysql并配置
``` shell
#进数据库初始化脚本以创建数据表
docker run --rm guacamole/guacamole /opt/guacamole/bin/initdb.sh --mysql > initdb.sql

#启动mysql-server
docker run --name mysqltest -e MYSQL_RANDOM_ROOT_PASSWORD=yes -e MYSQL_ONETIME_PASSWORD=yes -d mysql/mysql-server

#查看日志，获取密码（二者选其一）
docker logs mysqltest   #上方的命令执行后查找 [Entrypoint] GENERATED ROOT PASSWORD: 这个字段冒号后面是密码牢记，登录mysql时需要
docker logs mysqltest|grep GENERATED 

#重命名脚本并转移到已经运行的sql容器以便生成表
docker cp initdb.sql mysqltest:/guac_db.sql

#打开mysql终端
docker exec -it mysqltest bash

#登录mysql 
mysql -u root -p

#重新设定root用户密码
ALTER USER 'root'@'localhost' IDENTIFIED BY '123456';   #用户密码和路径可以自定义

#创建数据库以及创建用户 
CREATE DATABASE guacamole_db;   #（创建数据库）
CREATE USER 'root'@'%' IDENTIFIED BY '123456';  #（创建用户）
GRANT SELECT,INSERT,UPDATE,DELETE ON guacamole_db.* TO 'root'@'%';
FLUSH PRIVILEGES;    #（创建用户权限）
#创建完成后输入quit;退去

#使用脚本创建数据表 
cat guac_db.sql | mysql -u root -p guacamole_db     #需要输入用户的密码

#验证数据库操作是否成功
mysql -uroot -p             #(连接数据库)
USE guacamole_db;           #(选择数据库)
SHOW TABLES;                #(查看所有的表)
```

## 配置Guacamole服务器，Guacamole客户端
**启动guacd**
``` shell
docker run --name myguacd -d guacamole/guacd
```
**启动guacamole，并连接guacd，mysql**
``` shell
docker run --name myguacamole \
--link myguacd:guacd \
--link mysqltest:mysql \
-e MYSQL_DATABASE=guacamole_db \
-e MYSQL_USER=root \
-e MYSQL_PASSWORD="123456" \
-d -p 0.0.0.0:3300:8080 \
guacamole/guacamole
```
**查看运行状态**
``` shell
docker ps -a 
```  

## 访问已经运行的guacamole 
> http://host:3300/guacamole  
> 默认账户：guacadmin  
> 默认密码：guacadmin  