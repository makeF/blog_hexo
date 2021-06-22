## 介绍
* PlatformIO 是基于VScode扩展的IDE
* 可以有效利用vscode的代码补全、高亮、调试
* 编译比Aduino更高效
> 参考地址:  
> 安装 https://www.instructables.com/Develop-ESP32-With-PlatformIO-IDE/  
> 整体介绍 https://zhuanlan.zhihu.com/p/78722930  
> Blinker配置 https://blog.csdn.net/felix_tao/article/details/113359707
## 安装
1. VScode扩展中搜索platformio,安装插件    
2. 进入扩展设置取消勾选使用内置python  
3. 安装完成,点击newproject新建项目,进行PIO初始化  
   ![newproject](https://cdn.jsdelivr.net/gh/makeF/images/host/20210508003031.png)  
   稍作等待,PIO 会自动根据选择的 Board 和 Framework 配置工程并且下载需要用到的编译工具  
   
## 配置
1. **取消使用自带的python**
   ![不使用内置python](https://cdn.jsdelivr.net/gh/makeF/images/host/20210507235029.png)  
2. **安装外部库:** `C:\Users\UserName\.platformio\packages\`  
    > 安装Blinker:  
    > 1）打开网址https://www.diandeng.tech/doc/getting-start-8266，找到“下载并安装blinker Arduino库”，点击下载即可。  
    > 2）解压blinker-library-master.zip后，复制blinker-library-master到目录`C:\Users\UserName\.platformio\packages\framework-arduinoespressif8266\libraries`下  
3. **项目安装库**,修改`platformio.ini`  
   ![修改配置](https://cdn.jsdelivr.net/gh/makeF/images/host/20210507235604.png)  
   
   ``` ini
    #修改串口速度,及引用需要的库
    monitor_speed = 256000

    lib_deps = 
      adafruit/Adafruit Unified Sensor
      adafruit/DHT sensor library
   ```
4. **工具栏组合键**  
   ![工具栏](https://cdn.jsdelivr.net/gh/makeF/images/host/20210508001158.png)
   安装完成后,左下角会显示platform工具栏. 从左到右是： 
    * **主页**（PIO帐户，库和平台经理，董事会资源管理器等）  
    * **编译** <kbd>Ctrl+Alt+B</kbd>  
    * **上传** <kbd>Ctrl+Alt+U</kbd>（将构建的二进制文件部署到开发板）  
    * **清除**  
    * **串行端口监视器** <kbd>Ctrl+Alt+S</kbd>（与已部署的程序进行通信或调试）  
    * **PIO终端**（运行pio命令或与OS兼容的命令）   
5. **项目文件结构**   
   ![项目文件结构](https://cdn.jsdelivr.net/gh/makeF/images/host/20210508002517.png)  
   * `.pio/build`: 存放工程编译产生的文件  
   * `.pio/libdeps`: 导入配置文件中的库  
   * `src/main.cpp`: 程序主文件  
   * `platformio.ini`: 项目配置文件  