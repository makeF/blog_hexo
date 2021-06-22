``` shell
#安装邮件程序
apt install sendmail bsd-mailx

#配置邮箱
vim /etc/mail.rc

set from=**@163.com
set smtp=smtp.163.com
set smtp-auth-user=**@163.com
set smtp-auth-password=**   #授权码
set smtp-auth=login

#测试发送邮件
mail -s 'test' xxx@qq.com < /etc/passwd
```