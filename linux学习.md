# 网络连接

网络连接三种模式：

1.桥接模式：网段相同，但是最大能够到255  可能会超出这个范围 ，那么就会占用实际的IP地址

![image-20210512144225899](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210512144225899.png)

2.NAt模式：网络地址转换模式，虚拟地址可以和外部系统通信，不造成IP冲突，注意王五的虚拟机通过主机可以和外部通信，但是外部是无法连接到王五的虚拟机，注意下面是单箭头

![image-20210512144602109](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210512144602109.png)

3.主机模式：独立的系统



# 虚拟机克隆：

# 虚拟机快照:很有用

![image-20210512150950379](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210512150950379.png)



# window和centos共享文件夹、文件 

![image-20210512154706971](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210512154706971.png)

# linux目录结构

![image-20210512163753646](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210512163753646.png)

![image-20210513084106801](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210513084106801.png)

![image-20210513084000143](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210513084000143.png)

![image-20210513084453217](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210513084453217.png)

usr相当于window操作系统中的program files  ，是程序存放的位置，opt是主机额外安装软件的目录，相当于安装包存放的位置

/usr/local   这是另一个给主机额外安装软件所安装 的目录，一般是通过编译源码方式安装的程序

/selinux 是一种安全子系统，他能控制程序只能访问特定文件



# linux 实操篇：远程登录

查看linux服务器的IP地址的口令是：ifconfig    

在window中cmd指令查看IP地址的指令时：ipconfig  

查看window是否和远程的linux是否连接上 ，在window命令行中  输入  ping  后面加上linux的IP地址



## Xshell 和Xftp6 软件

其中xshell 软件是在window端通过命名行对linux服务器进行操作，不能进行文件的传输和下载  

Xftp6 可以进行文件的传输





# Vi和Vim编辑器

vi是内置的文本编辑器，相当于window中的记事本

vim是vi的增强版，代码补全  跳转错误 可以变换颜色 识别错误 程序员喜欢使用   

vim常用的快捷键：注意区分是正常模式 还是输入模式   还是命令行模式

![image-20210513112421137](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210513112421137.png)

三种模式的切换：

![image-20210513113827490](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210513113827490.png)

复制粘贴  ctrl + insert      和shift  + insert

# 关机和重启

![image-20210513141007091](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210513141007091.png)





# 普通用户登录和注销

![image-20210513135704810](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210513135704810.png)

假如以tom普通用户的身份登陆上去  ，然后 su - root  登录到超级用户，在超级用户输入logout 就会回到tom用户，如果在tom用户输入logout   是退出终端

如果使用xshell登录的话  logout就是退出当前账号 ，这是在centos终端不一样的

![image-20210513141051200](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210513141051200.png)

# 用户管理

![image-20210513141303903](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210513141303903.png)

有一个root账号，但是可以有多个普通用户，每个用户有自己对应的目录

在/home 目录下面有一个文件夹，叫tom  就是用户目录

## 添加用户

root权限下  命令行输入  useradd  milan 

会在/home  目录下面会自动生成，出现  milan文件夹

如果想指定生成的文件夹  指定的路径  

useradd  -d  /home/test   king   

这个新的用户名就是king ，用户目录就是  home下面的test文件夹

## 指定和修改账号密码

需要root权限 

passwd   加上用户名 

比如：passwd milan   就是修改milan用户的密码   如果后面不加上用户名的话就会修改当前用户的密码



## 删除用户

userdel  用户名

有下面两种情况：需要用root删除

1 删除milan用户，但是要保留家目录   userdel   milan

这种删除方法   milan 的家目录位于home下面仍然存在

2  删除用户以及用户主目录

userdel -r  tom    这个操作一定要慎重

细节说明 ： 是否要保留家目录，一般情况下建议保留



## 用户信息查询

id   加上用户名                    

比如  id  tom

由root 账号切换到普通账号时   su -  jack   

不需要输入密码



## 查看当前用户信息

who am i   或者whoami    

区别在于：who am i   显示的是“登录用户”的用户名，用户登录时的用过的id 

whoami：  显示的是当前“操作用户的”用户名



## 用户组



# 指定运行级别

运行级别3不带图形界面，可以节省很多资源

![image-20210514083739114](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210514083739114.png)

设置运行级别：

![image-20210514085215447](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210514085215447.png)

# 系统找回root密码

老韩的文档中写了详细的说明



# 帮助指令

man指令：man  【命令或者配置文件】

man  ls    展开之后页面太多   点击空格按键之后就会向下继续展开

在linux中隐藏文件是以  .  开头的，ls -a  会显示所有的文件  包括隐藏文件

ls命令可以组合使用，比如 ls  -al   a和l前后没有顺序区分

想要看下某个文件夹下的信息：

ls  -al    /home      后面加上路径信息

# pwd

显示绝对路径

./ 是当前路径    ../  父级目录

执行可执行文件的指令：  ./ a.out



# 家目录~

如果以root账号登录的话，那么家目录就是根目录下面的root目录     /root

但是如果是以其他账号登录的话 ，那么家目录就是在  /home/账号名    ,  这个路径下面。比如tom账号  那么家目录就是在/home/tom

新创建的账号就会在home账号下面生成一个目录，名称可以自己设置也可以默认为账号名】

![image-20210514103206581](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210514103206581.png)

# mkdir和rmdir 

创建目录，默认情况下创建一级目录

mkdir  /home/dog

但是如果想要创建多级目录的话  就需要加上选项

mkdir -p xx/yy的好处就是一次可以创建多级文件夹，若xx文件夹不存在，则先创建xx文件夹，然后在xx文件夹下创建yy文件夹

mkdir  -p   /home/animal/tiger

![image-20210514111608652](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210514111608652.png)

谨慎使用rm -rf  指令





# touch指令

![image-20210514111809669](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210514111809669.png)

这个指令和vim hello.txt   效果是一样的

如果要是删除的话   就不能使用rmdir  因为它是删除文件夹  也就是文件目录的指令，  可以使用rm  指令进行删除

# cp指令      ！

![image-20210514113144964](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210514113144964.png)

# rm指令！

![image-20210514114015861](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210514114015861.png)

# mv！指令

![image-20210514114203659](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210514114203659.png)

如果是同一个路径下的 就是重命名

如果不是同一路径下面  就是移动

mv可以移动文件或者整个目录都可以！！！！

# cat查看文件！

一些重要的文件查看使用cat指令 ，因为cat是查看不能修改文件内容



管道指令理解图示：

![image-20210514115406352](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210514115406352.png)

![image-20210514115628988](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210514115628988.png)



# more指令

more 指令可以单独使用，也可以管道连接时使用

more  /etc/profile  

![image-20210514120055882](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210514120055882.png)

# less 指令

比more更加强大，查看比较大的文件

![image-20210514133758321](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210514133758321.png)

# cal指令显示日历信息

直接输入cal即可

# ll 指令相当于ls -l  

# ls -lh    按照列表显示，并且h表示human就是人们能看懂的形式



# find 和grep查找的区别：

find是找到符合条件的文件路径

grep可以查找文件中的某个单词等

# 创建组

![image-20210514220758136](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210514220758136.png)



# chmod   usermod  chgrp  chown

chmod：改变文件/目录的权限

chgrp：修改文件/目录所在组

chown: 修改文件/目录所有者

usermod：改变用户所在组

# 目录权限的解释

![image-20210515112050247](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210515112050247.png)

当目录权限中没有r的权限时，假如这个目录中有一个文本文件是可以写的，那么即使没有r的权限 但是可以对这个文本文件进行写

# mkdir创建多级目录

![image-20210515115608974](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210515115608974.png)



# df-h查询磁盘使用结果  使用率大于80%就不太好了



# 普通文件  ll指令时前后是  “- ”开头，因此通过这个特点可以识别出普通文件

![image-20210515172937536](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210515172937536.png)

# 安装指令

![image-20210515173253698](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210515173253698.png)









# 网络连接

![image-20210521155648039](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210521155648039.png)



![image-20210521155721455](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210521155721455.png)

# DsystemNS的作用

![image-20210521160346865](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210521160346865.png)







# killall和kill进程

killall进程会终止这个进程以及所有的子进程



# ssh协议介绍

https://blog.csdn.net/uunubt/article/details/81509551?utm_term=ssh%E8%BF%9B%E7%A8%8B%E6%98%AF%E4%BB%80%E4%B9%88&utm_medium=distribute.pc_aggpage_search_result.none-task-blog-2~all~sobaiduweb~default-1-81509551&spm=3001.4430



# NFS介绍

**NFS (Network File System)即网络文件系统**，NFS允许一个系统在网络上与他人**共享目录和文件**。通过使用NFS，用户和程序可以像访问本地文件一样访问远端系统上的文件。

**NFS至少有两个主要部分：**一台服务器和一台(或者更多)客户机。当用户希望使用远程文件时，只要用“mount”命令就可以把远程文件系统挂在自己的文件系统之下，使远程的文件像本地计算机上的文件—样可以被访问。

在Windows平台下，同样可以支持NFS协议，并且有多个公司的NFS软件可以实现NFS方式的文件共享应用。



# Telnet协议

Telnet协议是[TCP/IP协议](https://baike.baidu.com/item/TCP%2FIP协议)族中的一员，是Internet远程登录服务的标准协议和主要方式。它为用户提供了在本地计算机上完成远程[主机](https://baike.baidu.com/item/主机/455151)工作的能力。在[终端](https://baike.baidu.com/item/终端/1903878)使用者的电脑上使用telnet程序，用它连接到[服务器](https://baike.baidu.com/item/服务器/100571)。[终端](https://baike.baidu.com/item/终端/1903878)使用者可以在telnet程序中输入命令，这些命令会在[服务器](https://baike.baidu.com/item/服务器/100571)上运行，就像直接在服务器的控制台上输入一样。可以在本地就能控制[服务器](https://baike.baidu.com/item/服务器/100571)。要开始一个telnet会话，必须输入用户名和密码来登录[服务器](https://baike.baidu.com/item/服务器/100571)。Telnet是常用的[远程控制](https://baike.baidu.com/item/远程控制/934368)Web[服务器](https://baike.baidu.com/item/服务器)的方法。





# 交换机和路由器  网关 

![image-20210528083847601](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528083847601.png)

![image-20210528084052588](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528084052588.png)

![image-20210528084136994](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528084136994.png)

![image-20210528084604781](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528084604781.png)

![image-20210528084641205](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528084641205.png)



![image-20210528084941736](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528084941736.png)



![image-20210528084846650](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528084846650.png)

![image-20210528085047233](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528085047233.png)





光猫可以直接连接电脑进行上网  光猫也具有路由器的功能

![image-20210528090757377](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528090757377.png)

# IP地址和mac地址

![image-20210528092019021](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528092019021.png)

![image-20210528092126682](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528092126682.png)

![image-20210528092225970](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528092225970.png)

![image-20210528092337238](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528092337238.png)

![image-20210528092939671](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528092939671.png)

## DHCP

*DHCP*（动态主机配置协议）是一个局域网的网络协议。指的是由服务器控制一段IP地址范围，客户机登录服务器时就可以**自动获得服务器分配的IP地址和子网掩码。**

![image-20210528092712061](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528092712061.png)

两台电脑之间进行通信： 是根据**arp**协议  

ARP协议是“**Address Resolution Protocol**”（地址解析协议）的缩写。其作用是在以太网环境中，数据的传输所依懒的是MAC地址而非IP地址，而将已知IP地址转换为MAC地址的工作是由ARP协议来完成的。

在局域网中，网络中实际传输的是“帧”，帧里面是有目标主机的MAC地址的。在以太网中，**一个主机和另一个主机**进行直接通信，必须要知道**目标主机的MAC地址**。但这个目标MAC地址是如何获得的呢？它就是通过**地址解析协议**获得的。所谓“地址解析”就是**主机在发送帧前将目标IP地址转换成目标MAC地址的过程**。ARP协议的基本功能就是通过目标设备的IP地址，查询目标设备的MAC地址，以保证通信的顺利进行。




![image-20210528093230638](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528093230638.png)

![image-20210528093536235](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528093536235.png)

# 家庭网络如何通过路由器上网？源地址转换和目标地址转换时什么？

![image-20210528094756779](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528094756779.png)



## 如何解决IP冲突问题：

![image-20210528094942004](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528094942004.png)



![image-20210528095221934](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528095221934.png)

![image-20210528095544772](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528095544772.png)

![image-20210528095451498](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528095451498.png)

![image-20210528095742199](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528095742199.png)

## Nat 分为   snat   和dnat

# TCP和UCP

![image-20210528100200632](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528100200632.png)

![image-20210528100539631](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528100539631.png)





# shelll脚本

、

![image-20210528123633000](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528123633000.png)

直接用相对路径  也可以用绝对路径执行



![image-20210528134947091](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528134947091.png)

输出的结果为   A=100

A=$A

A=100

还有 echo "A=$A"  输出结果也是  A=100       也就是说双引号不影响输出结果   就可以当没有双引号



## shell多行注释的写法



:<<!    内容      !



## 位置参数变量

比如： ./myshell.sh 100 200 , 这个就是一个执行shell 的命令行，可以在myshell 脚本中获取到参数信息

其中$0  就是命令本身    $1  就是100  以此类推

在myshell.sh文件中定义如下：

![image-20210528144303259](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528144303259.png)

变量A结果就是100   

$#  结果是参数的数目  在这就是两个变量

## 运算符

![image-20210528160806620](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210528160806620.png)



# MySql操作

1.show  databases

![image-20210530121146399](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210530121146399.png)



2. 创建数据库  create  database jzy ；   注意数据库内的相关操作 后面都要加上分号

   ![image-20210530121315313](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210530121315313.png)

3.使用数据库  use  数据库名

![image-20210530121424272](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210530121424272.png)



4.添加一个table 表

![image-20210530121519669](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210530121519669.png)

5.表中插入元素   insert into myorder values(100,'dog');

![image-20210530121711618](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210530121711618.png)

6.查看表内元素信息   select *  from myorder ；

![image-20210530121743180](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210530121743180.png)

# find和exec结合使用

exec选项后面跟随着所要执行的命令或脚本，然后是一对儿 {}，一个空格和一个\，最后是一个分号。 

  cmd {} \;

![image-20210530194909732](C:\Users\jiang\AppData\Roaming\Typora\typora-user-images\image-20210530194909732.png)

# 清空指令  echo ' '   > test.txt



# 关于cp的指令说明

**1、cp -rf /root/shtest/jzy/  /opt/zq/**

**2、cp -rf /root/shtest/jzy  /opt/zq**         

3、cp -rf /root/shtest/jzy/*   /opt/zq

1和2会把是把jzy这个文件夹拷贝到zq这个文件夹内   1和2效果是相同的

3不会把jzy这个文件夹拷贝到zq这个文件夹内，仅仅将jzy这个文件夹中的内容拷贝到zq这个文件夹内

复制一个文件的路径： Dir=$PWD 

cp -rf  /root/shtest/jzy    $Dir   注意这个Dir前面要加上$符号