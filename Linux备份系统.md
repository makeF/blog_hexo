## 备份
``` shell
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```
> `tar`当然就是我们备份系统所使用的程序了。
> `cvpfz`是tar的选项，意思是 `创建档案文件`、`保持权限`(保留所有东西原来的权限)、`使用gzip来减小文件尺寸`。
> `backup.gz`是我们将要得到的档案文件的文件名。
> `/`是我们要备份的目录，在这里是整个文件系统。
> `--exclude` 排除备份文件本身,及无需备份文件夹  

## 还原
* 切换到root用户，并把文件“backup.tgz”拷贝到分区的根目录下。 
* 恢复文件 `tar xvpfz backup.tgz -C /`  
* 创建排除掉的文件夹  
``` shell
mkdir proc
mkdir lost+found
mkdir mnt
mkdir sys
```
