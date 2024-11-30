进入到linux的界面，按一下↓键随后再按e键



找到以linux开头的那行，在做后面加上init=/bin/sh

随后 ctrl+x进入单用户模式

在光标闪烁的位置输入mount -o remount,rw/   回车

随后输入passwd 回车键之后会让你输入密码

！！！！注意在这里输入的密码是看不到的

输入一次，再重新输入一遍当出现下面这样就说明密码更改成功

![image-20241123133059149](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123133059149.png)

然后接着在闪烁的位置输入 touch /.autorelabel  回车

接着在光标闪烁处继续输入exec /sbin/init 回车，等待系统自动修改密码，完成后系统会自动重启，新的密码就生效了