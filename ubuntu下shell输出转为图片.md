## 安装软件
``` shell 
apt install enscript ghostscript imagemagick

#Enscript将ASCII文件转换为PostScript，HTML或RTF
#Ghostscript是一套建基于Adobe、PostScript及可移植文档格式（PDF）的页面描述语言等而编译成的免费软件。
#ImageMagick用来创建，编辑，撰写，或转换位图图像。

```

## 修改配置文件
可能会报 `the security policy` 错误
找到/etc/ImageMagick-*/policy.xml要转换的格式使用 `<!-- -->` 注释

``` xml
<policy domain="delegate" rights="none" pattern="pdf" />
<!-- 注释后 -->
<!--  <policy domain="delegate" rights="none" pattern="pdf" /> -->
```

## 使用
``` shell
#使用管道
enscript -B -p - demo.txt | ps2pdf - | convert -density 300 - output.png

#分步操作
enscript -p output.ps -B demo.txt
ps2pdf output.ps output.pdf 
convert -density 300 output.pdf output.png #可以省略,直接把output.ps转为图片,缺点是字体画质差
```