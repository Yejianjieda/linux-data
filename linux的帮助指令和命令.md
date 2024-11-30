# 帮助指令

man 获取帮助信息

基本语法 ： man 命令名称（功能描述：获得指定的命令的帮助信息）

案例： 查看ls命令的帮助信息 man ls

![image-20241123135327658](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123135327658.png)

比如-a参数： 列出当前目录下面的隐藏文件（注意：linux操作系统下面的隐藏文件都是以.开头的）。

ls -a

比如-l参数：以列表的形式展示指定目录下面的文件。

我们还可以将参数组合起来使用

ls -la

help 获得shell内置命令的帮助信息





# linux常用命令

## linux文件（目录）相关的指令

### 1. 文件（目录）操作

在linux操作系统里面，获取文件的方式有两种，一种是通过绝对路径的方式获取文件，一种是相对路径

获取文件。

假设我们在当前指定的目录下面，想要获取指定的文件，我们可以通过相对路径和绝对路径的方式来获取。

![image-20241123140134478](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123140134478.png)

pwd指令 显示当前目录的绝对路径

ls指令 显示当前目录下面的所有文件

常用选项：

~：cd~ 回到当前用户的home目录（如果是root用户）那么就是回到root目录下面，如果非root用户，那么就回到home/用户目录下面）

![image-20241123140317759](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123140317759.png)

/:cd /回到系统根目录

cd ..回到当前目录的上一级

例子： 比如我们现在所在的目录是/home/kobe目录。现在我们要使用回到/root目录下面去。

cd ../../root

![image-20241123140422651](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123140422651.png)

cd -回到上一条命令所在的目录

![image-20241123140509338](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123140509338.png)

直接切换到指定目录

比如我们现在所在的目录是/home/kobe目录，现在我们要使用回到/root目录下面去

![image-20241123140606705](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123140606705.png)

.mkdir ：用于创建目录

![image-20241123140639232](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123140639232.png)

此时报错，因为我们创建多级目录的时候，需要携带一个-p参数。

 -p 创建多级目录。我们可以这样创建多级目录

![image-20241123140651685](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123140651685.png)

rmdir：指令删除空目录

需求：我们删除dog目录

![image-20241123140733477](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123140733477.png)

![image-20241123140741985](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123140741985.png)

touch：创建空文件

![image-20241123140803414](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123140803414.png)

cp：拷贝文件到指定目录

![image-20241123140912462](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123140912462.png)

-r 递归复制整个文件夹

![image-20241123140935097](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123140935097.png)

rm ：移除文件或目录

-r 递归删除整个文件夹

-f 强制删除不提示

mv ：移动文件（剪切）或重命名

![image-20241123141038599](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123141038599.png)

![image-20241123141049358](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123141049358.png)



### 2.查看操作

**cat** 查看文件内容 cat [选项] 要查看的文件

需求：查看/etc/profile文件，并显示行号

-n 显示行号 cat -n /etc/profile

```linux
[root@xq100 guojing]# cat -n /etc/profile #浏览文件 并显示行号
```

cat只能浏览文件，并不能修改文件，为了浏览方便，一般会用上管道命令 |more。

```
[root@xq100 guojing]# cat -n /etc/profile | more #浏览文件 并显示行号 分屏幕显示 使
用空格键可以翻页显示
```

**more** more指令是一个基于vi编辑器的文本过滤器，他以全屏的方式显示文本文件的内容，more

指令内置了若干快捷键。

```
[root@xq100 guojing]# more /etc/profile
```

![image-20241123141331666](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123141331666.png)



**less**

 less指令用于来分屏查看文件内容，他的功能与more类似，但是比more更加强大，支持各种显示终

端。less指令在显示文件内容时，并不是一次将整个文件加载后才显示的，而是根据要加载的内容，**对**

**显示大型文件具有高效率。**

语法： less 文件名称

```
[root@xq100 guojing]# less /etc/profile
```

![image-20241123141350362](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123141350362.png)

**echo**:将输入内容到控制台

需求1：使用echo指令输出环境变量。

```
[root@xq100 guojing]# echo $PATH # 输出环境变量
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin
[root@xq100 guojing]# echo $HOSTNAME # 输出主机名称
xq100
```

![image-20241123141546083](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123141546083.png)

**head**: head用于显示文件开头部分内容，默认情况下head希纳是文件前10行的内容

基本语法： head 文件

 head -n 5 文件 显示前五行的内容 5可以是任意数

```
[root@xq100 guojing]# head /etc/profile # 默认显示前10条内容
[root@xq100 guojing]# head -n 5 /etc/profile # 默认显示前5行内容
```

**tail****指令** 用于输出文件中尾部的内容，默认情况下tail指令显示文件的前10行内容

 tail 文件 （查看文件最后10行的内容）

 tail -n 5 文件 （查看文件最后5行的内容，5可以是任意数）

 tail -f 文件 （实时监控文件发生的变化）

```
[root@xq100 guojing]# tail /etc/profile # 显示最后10行的数据
[root@xq100 guojing]# tail -n 5 /etc/profile #显示最后5行的数据
```

需求：创建一个空文件test.txt。实时监控这个文件的变化

```
[root@xq100 guojing]# touch test.txt
[root@xq100 guojing]# tail -f test.txt
```

在另一个终端，我们向test.txt文档追加内容

![image-20241123141753708](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123141753708.png)

 `> `指令和 `>>` 指令： `>`输出重定向 ，`>>`追加

 echo ‘hello’ > /home/guojing/test.txt （将hello输入到guojing文件夹下的test.txt中 之前内容覆

盖）。

 echo ‘hello’ >> /home/guojing/test.txt （将hello追加到guojing文件夹下的test.txt文件的末尾处 之前

内容不会覆盖）。

 cat /etc/profile > /home/guojing/myprofile （将etc/profile 重定向到home目录下的myprofile 没有

会自动创建）

 cal > /home/guojing/test.txt （将日历信息重定向输出到opt下的test文件）覆盖

 cal >> /home/guojing/test.txt（将日历信息追加到opt目录下的test文件）追加

软连接

软连接也称为符号链接，类似中windows里面的快捷方式，主要是存放了链接文件的路径。

ln -s [源文件或目录] [软连接名称]

我们在/home目录下创建一个软连接linkToRoot 链接到/root目录

![image-20241123141900274](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123141900274.png)

**history****指令** 查看用户已经执行过的历史指令

![image-20241123142023725](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241123142023725.png)



### 3.linux时间指令

date指令：

基本语法:

date（功能描述：显示当前时间）

date +%Y（功能描述：显示当前年份）

date +%m（功能描述：显示当前月份）

date +%d（功能描述：显示当前是哪一天）

date "+%Y-%m-%d %H:%M:%S"（功能描述：显示年月日时分秒）

```
[root@xq100 ~]# date
Sun Aug 28 15:41:39 CST 2022
[root@xq100 ~]# date +%Y
2022
[root@xq100 ~]# date +%m
08
[root@xq100 ~]# date +%d
28
[root@xq100 ~]# date "+%Y-%m-%d %H:%M:%S"
2022-08-28 15:43:59
```



date指令也可以设置日期

基本语法：date -s 字符串时间

```
[root@xq100 ~]# date -s "2022-8-28 15:48:50"
```

cal日历指令

cal 显示当月的日历

cal 年份 #显示当前年的所有日历



### 4.搜索查找

- find将从指定目录下递归地遍历各个目录，将所有满足条件的目录显示在控制台

find [搜索范围][选项]

| 选项  | 功能                   |
| ----- | ---------------------- |
| -name | 按照文件的名称查找文件 |
| -user | 查找指定用户所属的文件 |
| -size | 按照指定的大小查找文件 |

实例1：按照文件名称查询文件

```
[root@xq100 kobe]# find /home/kobe -name 'Hello.java' # 查询/home/kobe目录下面 名
称为Hello.java的文件
/home/kobe/Hello.java
[root@xq100 kobe]# find /home/kobe -name '*.java' # 查询所有java文件
/home/kobe/Hello.java
/home/kobe/Demo1.java
```

实例2 ： 在/opt目录下，查询root用户创建的文件

```
[root@xq100 kobe]# find /opt -user 'root'
```

实例3： 查找整个linux系统下，大于200m的文件

```
[root@xq100 kobe]# find / -size +200M #查询大于200M的文件
/run/media/root/CentOS 7 x86_64/LiveOS/squashfs.img
[root@xq100 kobe]# cd /run/media/root/CentOS\ 7\ x86_64/LiveOS/
[root@xq100 LiveOS]# ls -lh # 以友好的形式显示文件信息（很容易查看文件大小）
total 476M
-rw-r--r--. 1 root root 476M Sep 6 2019 squashfs.img
-r--r--r--. 1 root root 224 Sep 12 2019 TRANS.TBL
```

- locate指令 locate指令可以快速定位文件路径。locate指令利用事先建立好的系统中所有文件名

  称及路径的locate数据库实现快速定位给定的文件。**locate指令无需遍历整个文件系统，查询速度较快。**

**特别说明：**

由于locate指令基于数据库进行查询。所以第一次查询运行前，**必须使用****updatedb****指令创建****locate****数**

**据库。**

需求：用locate指令快速定位 Hello.java 文件所在目录 locate Hello.java

```
[root@xq100 ~]# updatedb # 一定要先执行这个指令
[root@xq100 ~]# locate Hello.java # 快速定位Hello.java文件所在的目录并输出
/home/kobe/Hello.java
/root/Hello.java
```

**which**指令 可以查看某个指令在哪个目录下，

查看ls指令在那个目录 which ls

查看reboot指令在那个目录下 which reboot

```
[root@xq100 ~]# which ls # 查看ls指令所在的目录
alias ls='ls --color=auto'
/usr/bin/ls
[root@xq100 ~]# which reboot # 查看reboot指令所在的目录
/usr/sbin/reboot
```

- grep指令

grep过滤查找，管道符，”|“,表示前一个指令的处理结果输出传递给后面的指令处理。一般我们将 | 和

grep一起结合起来使用。

基本语法：grep [选项] 查找内容 源文件

| 选项 | 功能           |
| ---- | -------------- |
| -n   | 显示行号       |
| -i   | 忽略自动大小写 |

案例：查找在/home/kobe目录下的Hello.java文件中，查找hello所在行，并显示行号。

```
[root@xq100 kobe]# cat Hello.java |grep -ni 'Hello'
```

![image-20241130111547491](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241130111547491.png)



### 解压缩指令

.gz 格式的压缩文件 

gzip用来进行文件的压缩

gunzip 解压



.zip 压缩文件

zip 压缩  对文件目录 -r

unzip 解压



.tar.gz格式的压缩文件

tar命令 既可以压缩文件也可以解压文件

-c 产生tar文件(打包文件)

-v 压缩和解压的时候显示对应的详细信息

-f 指定压缩后的文件名 

-z 打包的同时并压缩

-x 压缩tar包文件



压缩文件的命令 tar -zcvf 压缩文件的名称 目录

解压文件的命令 tar -zxvf 压缩文件的名称

![image-20241130113923103](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241130113923103.png)













































































