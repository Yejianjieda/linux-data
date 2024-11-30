# 用户管理

注意：创建用户的权限只有管理员才有 ， 我们一般在root用户下面去创建用户

useradd 用户名  

useradd -d 目录名称 用户名  创建用户的的同时自定义用户目录的名称

给用户设置密码 passwd kobe 给指定的用户设置密码

userdel 用户名 删除用户数据的同时也会删除用户的目录

id 用户名称 查询用户信息



查询用户信息

linux系统是一个多用户多任务的操作系统，任何一个要使用系统资源的用户，都必须首先向系统管理员

申请一个账号，然后以这个账号的身份进入系统。

## **1.6.1** **添加用户**

在root用户下，我们可以创建很多其它的用户，并且这些用户都会生成对应的目录，这些目录位

于/home/用户名的目录下面。如果我们使用自己创建的用户登录，默认的情况下，用户所在的目录就

是/home/用户目录所在的位置。

如何创建用户? useradd [选项] 用户名

细节：

当用户创建成功后，会自动的创建和用户同名的目录。这个目录位于/home下面。

也可以通过 useradd -d来指定目录新的用户名，给新的用户名指定目录

## **1.6.2** **给用户添加密码**

创建密码的命令： passwd 用户名

我们执行logout指令，然后使用kobe进行登录，发现可以成功登录。

## **1.6.3** **删除用户**

删除用户有两种情况，一种是删除用户，保存用户对应的目录。还有一种是删除用户，连用户对应的目

录也删除掉。

删除用户，保存用户对应的目录 

userdel 用户名

注意，我们切换到root用户下面，执行用户的删除操作。

[root@xq100 ~]# useradd kobe #创建用户名为kobe的用户

[root@xq100 ~]# cd /home # 切换到home目录

[root@xq100 home]# ll # 查看home目录所在的文件夹

total 0

drwx------. 3 kobe kobe 78 Aug 27 17:49 kobe

drwx------. 5 xq xq 147 Aug 27 16:02 xq

[root@xq100 home]# useradd -d /home/test king # 创建一个用户名为king的用户 用户目录位

于/home/test

[root@xq100 home]# cd /home

[root@xq100 home]# ll

total 0

drwx------. 3 kobe kobe 78 Aug 27 17:49 kobe

drwx------. 3 king king 78 Aug 27 17:52 test

drwx------. 5 xq xq 147 Aug 27 16:02 xq

[root@xq100 home]# passwd kobe # 给kobe这个用户设置密码

Changing password for user kobe.

New password:

BAD PASSWORD: The password is shorter than 8 characters

Retype new password:

passwd: all authentication tokens updated successfully.删除用户，对应的用户目录也删除掉 

userdel -r 用户名

## **1.6.4** **查询用户信息**

查询用户的详细信息

id 用户名

uid: 用户id gid：用户组id groups：组名

查看当前的用户的信息

who am i / whoami

切换用户

su 用户名

注意：从高级别的用户切换到低级别的用户不需要输入密码。比如从root切换到kobe用户。

从低级别的用户输入到高级别的用户，需要输入密码。必须从kobe用户切换到root用户。

## 1.6.5用户组

用户组类似于角色，系统可以对有共性(权限)的多个用户进行统一管理。我们可以通过下面一幅图来理解组的概念。

![image-20241116154659220](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241116154659220.png)



创建 、 删除用户组

groupadd 组名

groupdel 组名   删除一个组

增加用户的时候，直接指定组名称

之前我们创建用户的时候，没有指定组，其实系统会自动给用户分配一个组，这个组的名称和用户名称是一样的。

现在我们创建用户的时候直接指定组名称。

基本语法： useradd -g 用户组 用户名

![image-20241116154834082](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241116154834082.png)

修改用户所在组

比如我们之前有一个用户guojing，所在组为gaibang。现在我们想将guojing这个用户放在taohuadao

这个组里面去（前提是这个组必须存在）。

基本语法： usermod -g 用户组 用户名

![image-20241116154848812](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241116154848812.png)

用户和组相关的文件

（1）/etc/passwd文件

用户的配置文件，记录用户的各种信息。

每行的含义：用户名：口令：用户标识号：组标识号：注释性描述：主目录：登录shell

使用cat命令浏览这个文件： cat /etc/p

![image-20241116154858733](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241116154858733.png)

/etc/shadow文件

口令的配置文件，用户登录的时候需要口令(密码)。口令的验证都是通过这个shadow文件去验证的。

每行的含义：登录名：加密口令：最后一次修改的时间：最小时间间隔：最大时间间隔：警告时间：不

活动时间：失效时间：标志

![image-20241116154921967](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241116154921967.png)

我们发现guojing这个用户没有加密口令，所以没有显示。我们给guojing这个用户设置密码就可以看到加密口令了。

![image-20241116154942726](C:\Users\20655\AppData\Roaming\Typora\typora-user-images\image-20241116154942726.png)

（3）/etc/group文件

组的配置信息，记录linux包含的组的信息

每行含义：组名：口令：组标识号：组内用户列表







