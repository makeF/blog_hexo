### 参考文档
[代理转发](https://toutyrater.github.io/advanced/outboundproxy.html)  
[路由功能](https://www.v2ray.com/chapter_02/03_routing.html)  

### 安装xray
`bash <(curl -sL https://s.hijk.art/xray.sh)`  
[完整配置示例](https://cdn.jsdelivr.net/gh/makeF/images@master/files/xray_routing_config.json)  
### 修改配置文件

``` shell
vim /usr/local/etc/xray/config.json
```
``` json
//1.在"butbounds"节点下添加中转服务tag
{
    "tag": "vir",   //标记名称
    "protocol": "shadowsocks",  //中转服务类型
      "settings": {         //参数
        "servers": [
          {
            "address": "ip address",
            "method": "aes-128-gcm",
            "ota": false,
            "password": "passwd",
            "port": 1080
          }
        ]
      },
    "sniffing": {   //嗅探流量
      "enabled": true,
      "destOverride": ["http", "tls"]
    },
    "mux": {
      "enabled": false,
      "concurrency": -1
    }
}

//2.在"routing" => "rules" 下添加路游规则
{
    "type": "field",    //目前只支持"field"
    "domain": ["pornhub.com"],  //需要中转的网址,"domain","ip"任选其一就行
    "outboundTag": "vir"    //前面节点的名字
}
```
### 生效配置
``` shell
systemctl restart nginx xray
```