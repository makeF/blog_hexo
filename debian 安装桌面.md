## 安装中文环境
``` shell
# 设置时区
timedatectl set-timezone Asia/Shanghai
# 查看当前时区
timedatectl

# 安装中文环境
dpkg-reconfigure locales
# 查看安装
locale -a
# 安装中文字体
apt-get install ttf-wqy-zenhei
apt-get install xfonts-intl-chinese wqy*

```
## 安装桌面程序
``` shell
# 安装X11和一个桌面环境，它将作为Xrdp的后端。
apt update 
apt install xfce4 xfce4-goodies xorg dbus-x11 x11-xserver-utils
# 安装Xrdp
apt install xrdp 
# 执行以下命令将xrdp用户添加到组
adduser xrdp ssl-cert   #秘钥登录相关?
```
xrdp配置文件 `/etc/xrdp/xrdp.ini`  
连接不上,尝试放开防火墙3389端口
## 安装常用程序
### 安装输入法
``` shell
# 安装fctix
apt install fcitx
apt install --fix-broken

#apt install fcitx-googlepinyin #google拼音
#apt install fcitx-sunpinyin #sun拼音
# 搜狗输入法 下载:https://pinyin.sogou.com/linux/
dpkg -i sogoupinyin-*.deb
```
### 安装浏览器
``` shell
# 轻量浏览器midori
install midori

# firefox
echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | tee -a /etc/apt/sources.list > /dev/null
apt update
# 提示没有公钥,复制公钥
apt-key adv --recv-keys --keyserver keyserver.ubuntu.com CCC158AFC1289A29
apt update
```