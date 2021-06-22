优缺点:  
* 界面漂亮,硬件需求理论很低  
* 漂亮的linux桌面  
* linux使用容器,不知道性能咋样  
* 进系统需要代理  
  
参考:  
* https://baijiahao.baidu.com/s?id=1672435449789322394  
* https://sspai.com/post/61056/  
----

## 下载准备资源
> 提前准备U盘、PC  
1. [Ubuntu Mate 20.04](https://ubuntu-mate.org/download/amd64/) 用来辅助安装  
2. [Rufus](http://rufus.ie/zh/) 刷写启动盘  
3. [ChromeOS镜像](https://cros-updates-serving.appspot.com/)  Intel处理器 3代以下搜索'samus',以上搜索'rammus'  
4. [Brunch](https://github.com/sebanc/brunch/releases) ChromeOS安装、启动工具包  

## 制作启动盘
1. 使用 Rufus 制作 Ubuntu 启动盘,注意选择GPT分区UEFI启动  
2. 制作完成后,进入U盘创建'ChromeOS'文件夹  
3. 把 ChromeOS镜像 及 Brunch工具包 解压至创建的文件夹  

## 安装ChromeOS
1. 进入电脑BIOS设置为UEFI启动  
2. 插入U盘,进入Ubuntu系统,无需安装  
3. 连接网络,进入ChromeOS文件夹 `cd /cdrom/ChomeOS`  
4.   
   ``` shell
    # 安装依赖 
    sudo apt update && sudo apt install figlet pv cgpt
    # 查看硬盘,一般为 /dev/sda
    sudo fdisk -l
    # 在ChomeOS文件夹打开终端,安装chromeos
    sudo bash chromeos-install.sh -src chromeos_***.bin -dst /dev/sda #自行替换bin文件名及安装位置
   ``` 
5. 重启进入系统

## 配置设置
* 开机进入MDK  
  > 进入本地磁盘,选择密钥进行开机  
* 登录账号设置代理  
  > 自行设置旁路由,同局域网手机挂vpn  
* 开启linux容器  
  > 右下角, 设置 -> 高级 -> 开发者 -> 启用linux开发环境  
