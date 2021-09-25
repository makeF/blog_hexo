## shopt 可以设置shell参数  
``` shell
shopt [-psu] [optname]
```  
> -s 开启某个选项.
> -u 关闭某个选项.
> -p 列出所有选项的当前生效命令. （不带-p表示列出所有选项的当前状态）

## 选项设置
### extglob选项
``` shell
shopt extglob #查看extglob选项是否开启
shopt -s extglob #开启extglob选项
```
**模式选项**
``` shell
?(pattern-list)      #所给模式匹配0次或1次
*(pattern-list)      #所给模式匹配0次以上包括0次
+(pattern-list)      #所给模式匹配1次以上包括1次
@(pattern-list)     #所给模式仅仅匹配1次
!(pattern-list)       #不匹配括号内的所给模式
```