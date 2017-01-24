**linux严格区分大小写**

####切换到root账户
- 方法一 ：su root   切换到root用户
- 方法二： su 
- 方法三：su -

**`su 用户名`  切换到指定账号**，`su dy`   切换为用户 dy

root可以无密码切换到任何账号，而其他账号切换需要密码

dhclient   获得一个动态的IP

linux里root的权限最高，建议平时用普通用户，安装软件和分配账号时可以用root，linux也可以有多个root

etc文件夹 为配置文件夹

####/home
/home存有所有账号的家目录(root除外)，一个账号一个家目录，

在任何账号下执行`cd`命令即到当前用户的家目录

家目录可以放置各自的信息，新建的账户的家目录是空的
####/lib

lib为标准程序设计库，又叫动态链接共享库，作用类似windows里的.dll文件 

/lib目录是根文件系统上的程序所需的共享库，存放了根文件系统程序运行所需的共享文件。这些文件包含了可被许多程序共享的代码，以避免每个程序都包含有相同的子程序的副本，故可以使得可执行文件变得更小，节省空间。

####/boot
/boot目录存放引导加载器(bootstrap loader)使用的文件，如lilo，核心映像也经常放在这里，而不是放在根目录中。但是如果有许多核心映像，这个目录就可能变得很大，这时使用单独的文件系统会更好一些。还有一点要注意的是，要确保核心映像必须在ide硬盘的前1024柱面内。 

####/mnt
/mnt目录是系统管理员临时安装(mount)文件系统的安装点。程序并不自动支持安装到/mnt 。/mnt下面可以分为许多子目录，例如/mnt/dosa 可能是使用msdos文件系统的软驱，而/mnt/exta 可能是使用ext2文件系统的软驱，/mnt/cdrom光驱等等。 

####/dev
/dev目录存放了设备文件，即设备驱动程序，用户通过这些文件访问外部设备。比如，用户可以通过访问/dev/mouse来访问鼠标的输入，就像访问其他文件一样。 
usr字体帮助文档目录

var 邮件www目录

ctrl+C终止当前命令

shell 用户与内核沟通的中间人

图形化shell--gui
命令行shell--cli


##命令行--命令+选项+参数

ls 显示当前目录文件

ls -l  详细显示当前目录，简写形式为ll

ls -l /root  显示root目录的详细文件

ctrl+l 或者 clear 清零结果显示

ls / 显示文档根目录文件和文件夹信息

ls -l / 详细显示

date  显示当前的日期和时间 年月日时分秒 星期二 东八区

date "+%Y-%m"  指定日期显示格式

date "+%Y-%m-%d %H:%I:%S"

yum search tree  安装目录树

cal  显示当前年月日日历

cal 18 3 2010  显示2010年3月18日的日历

cal 2010 显示2010全年的日历

ctrl+alt+f1~f5 切换终端界面

ctrl+shift+=  放大终端界面

ctrl+shift+-  缩放终端界面

`useradd 用户名` 增加一个用户 只能由root操作

`passwd 用户名` 为用户设置密码

`passwd dy` 为用户dy更改密码  要root权限才能改

tab键能够自动补全

连按两下tab键 可以看到总共有的命令的总数

ctrl+c 放弃刚才打入的行或正在执行的命令

####exit和ctrl+d
exit  退出当前shell

ctlr+d   退出当前shell，与exit功能一样

#### man 列出命令的详细说明文档 
man date 列出date命令，精简版没有man命令

#### shutdown
shutdown -h now    立刻关机，需要root权限或者配置相应权限


shutdown -r now    是重启

shutdown -h +10 "10 i shutdown"  10分钟后关闭并发送广播

cd  不家任何参数则为进入当前用户的家目录

cd  /home  进入系统的家目录，存放所有用户的家目录，只能进入自己的家目录，不能进入其他用户的家目录

reboot  重启，需要root权限

####who
who 查询当前连接linux的用户


账号（用户）user
角色（用户组）group
其他人other


`[daiyan9095@bogon Desktop]$ cd`  回到当前用户的home文件夹

`[daiyan9095@bogon ~]$ cd /tmp`   进到tmp文件目录，要带斜线

`[daiyan9095@bogon ~]$ yum search tree`  安装软件之前先搜索软件源

`[daiyan9095@bogon tmp]$ pwd`  显示当前目录

`[daiyan9095@bogon ~]$ touch houdunwang.php`  在家目录里建立一个空文件

`[root@bogon daiyan9095]# exit`   退出root的shell,回到之前用户的shell，等同于`ctrl+d`

`[daiyan9095@bogon ~]$ ls -l houdunwang.php`  显示文件的详细信息,等同于`ll houdunwang.php`

`[daiyan9095@bogon ~]$ ls -il` 查看当前用户所有文件的id号,又如：
`[root@bogon home]# ll -i daiyan9095`


-rw-rw-r--. 1 daiyan9095 daiyan9095 0 Jun 13 16:49 houdunwang.php

	解释：-为文件类型，表示一个普通文件，若是d的话则为目录
    后面的各位表示权限，3个为一个单位
    前三个rw-指的是所有者daiyan9095的权限 u
    中间的3个rw-指的是所有组的权限 g
    后边的三个r--代表的是其他人 o
r代表可读，w代表可写， 这个-代表执行(属性为不能执行) 若为x则为可以执行    

      1表示链接数，daiyan9095表示用户（创建者），后边的daiyan9095为用户组，
      0 表示文件的大小 使用ls -lh则输出的是kb表示的大小
      Jun 13 16:49为文件的修改时间

`[daiyan9095@bogon ~]$ echo "abc">>houdunwang.php`  将abc追加到文件内部

`[daiyan9095@bogon ~]$ echo "abc">>houdunwang.php`  重写文件为abc，原有内容全部删除

`[daiyan9095@bogon ~]$ cat houdunwang.php`  输出文件内容

`[root@bogon www]# tail -100 top.log` 查看文件的末尾100行数据

`[root@bogon www]# head -100 top.log` 查看文件的开头100行数据 

`[daiyan9095@bogon ~]$ vim houdunwang.php`  使用vim查看文件内容

`[daiyan9095@bogon ~]$ vi houdunwang.php`  使用vi查看文件内容

在linux中的以.开头的文件就是隐藏文件 

`[daiyan9095@bogon ~]$ ls -a`   显示所有的文件，包括隐藏文件

`[daiyan9095@bogon ~]$ ls -ai`  包含文件ID

`[daiyan9095@bogon ~]$ mkdir abc`   在当前目录下新建一个文件目录abc

`[daiyan9095@bogon ~]$ rmdir abc` 删除当前目录里的abc目录

`rm` 为移除文件，但当`rm -rf` 时，既可以移除文件也可以移除目录

`[daiyan9095@bogon ~]$ touch a`  在当前目录下新建立一个a目录

`[daiyan9095@bogon ~]$ umask -S` 输出文件创建时设置的默认权限

权限的数字表示：
    r=4  w=2  x=1

-rwxrwxrwx  权限：777 

`[daiyan9095@localhost ~]$ umask`  不带参数 -S的话会以数字的形式表示文件的权限，这里得到的值为0002,可以使用减法，7-0=7 7-0=7 7-0=7 7-2=5 同样能得到文件的权限信息

`[daiyan9095@localhost ~]$ umask -S`  则结果为u=rwx g=rwx o=rx 

`[daiyan9095@localhost ~]$ mkdir b`   在当前文件目录下建立b目录

此时的详细信息：drwxrwxr-x. 2 daiyan9095 daiyan9095 4096 Jun 14 07:49 b
说明对目录给予了x的权限，4096为文件目录的默认创建大小


[daiyan9095@localhost ~]$ cd /tmp   进到临时目录

[daiyan9095@localhost tmp]$ mkdir dy  创建目录  dy 

[daiyan9095@localhost tmp]$ cd dy  进入到dy 目录下

[daiyan9095@localhost dy]$ touch a/1.php  在tmp下的dy里的a下放置一个文件1.php，前提是dy下存在a文件目录 

-rw-rw-r--. 1 daiyan9095 daiyan9095 0 Jun 14 07:59 1.php  该文件的信息



-rwxrwxrwx. 1 daiyan9095 daiyan9095 0 Jun 14 07:59 1.php  加完权限后的信息

[daiyan9095@localhost a]$ echo "hello world">>1.php  在1.php里追加写入hello world 

[daiyan9095@localhost a]$ cat 1.php   输出 1.php的内容 

以上的权限仅指的是文件的内容，与文件自身无关，要看文件是否可删要看其目录的权限 

drwxrwxr-x. 2 daiyan9095 daiyan9095 4096 Jun 14 07:59 a   看到其他人对目录仅有读的权限而没有写的权限，因此不能删除a下的文件 

exit  退出当前的shell，相当于ctrl+d



####目录的rwx 
- w 表示新建文件和删除文件移动文件，即增删改
- r 表示读取目录
- x 表示能够进入到目录里面 

####chmod   改变文件权限  
`[daiyan9095@localhost a]$ chmod 777 1.php`   更改1.php的权限 

`[daiyan9095@localhost dy]$ chmod 770 a`  

**改变a的权限，要在其父目录里面改**

[daiyan9095@localhost dy]$ hostname   显示主机名 

**[daiyan9095@localhost qq]$ chmod u=rw sina**   更改所有者的权限为rw即6

**[daiyan9095@localhost qq]$ chmod g=r sina**   单独更改所有组的权限

**[daiyan9095@localhost qq]$ chmod o=rwx sina**   单独更改其他人的权限 

**[daiyan9095@localhost qq]$ chmod o=rwx,g=rwx sina**  更改其他人和组的权限

**[daiyan9095@localhost qq]$ chmod o-w sina** 使得其他人对文件不具有w的权限

**[daiyan9095@localhost hd]$ chmod u-r,g-r,o-r baidu**  去掉用户的r权限 

**[daiyan9095@localhost hd]$ chmod -r baidu**  去掉所有者的r权限，即不指定时默认为所有者

**[daiyan9095@localhost dy]$ chown qq index.php** 将index.php的所有者改为qq 

**[daiyan9095@localhost dy]$ chown qq:qq index.php** 改变index.php的所有者和所有组 

`rm `文件名 删除文件
`rmdir` 目录名 删除目录，此目录必须为空 
`rm -rf`  递归删除文件目录，可以作用于文件和目录

**[root@localhost tmp]# mkdir -p www/admin/tpl** 递归创建目录  
  
**[root@localhost www]# chown -R** daiyan9095:daiyan9095 admin 递归的将admin即其子目录和文件改变所有者和所有组


####递归:
	-p 创建目录时
	-r 删除目录时
	-R 更改目录及其包含文件所有者/组时

`.`代表当前目录
`..`代表上一级目录


[daiyan9095@localhost ~]$ cd .  还是当前目录

[daiyan9095@localhost ~]$ cd .. 进入到上一级目录

[daiyan9095@localhost ~]$ ls .  显示当前目录

[daiyan9095@localhost ~]$ ls ..  显示上一级目录

[daiyan9095@localhost ~]$ ls ../.. 显示上上一级的目录 

[daiyan9095@localhost a]$ ls -l ..

[daiyan9095@localhost a]$ ls -l ../..

[daiyan9095@localhost a]$ ls ../../dy

[daiyan9095@localhost ~]$ cd ~  进入当前用户的家目录 

[daiyan9095@localhost ~]$ cd -  在之前的工作目录之间进行切换 

`[daiyan9095@localhost ~]$ echo $PATH`  输出linux的环境变量

**[daiyan9095@localhost ~]$ PATH=$PATH:/daiyan9095**  增加环境变量，一定要带着原来的$PATH否则重写了

**[daiyan9095@localhost ~]$ ./houdunwang.php**  没有增加当前目录的环境变量的话要执行当前目录下的文件就要加./

####dirname 取得父级目录

	[root@bogon www]# dirname /tmp/www/top.log 
	/tmp/www


####basenam取得文件的名字

    [daiyan9095@localhost ~]$ basename ~daiyan9095

**[daiyan9095@localhost ~]$ ls -lh** 按kb表示文件的大小显示文件信息

####-S 排序，降序
**[daiyan9095@localhost ~]$ ls -lhS** 以文件大小降序显示

**[daiyan9095@localhost ~]$ ls -lhSr** 以文件大小升序显示

**[daiyan9095@localhost ~]$ ls -la** 显示所有文件，包括隐藏文件

**[daiyan9095@localhost ~]$ ls -ltS**  按时间降序排列

[daiyan9095@localhost ~]$ mkdir ~/html  在自己家创建一个html目录 

[daiyan9095@localhost ~]$ rm -rf a  删除a及其下的所有文件

**[daiyan9095@localhost ~]$ rm -r a/b/c**  询问递归删除目录

#7 

移除目录  rmdir

移除文件 rm ，当加上参数-rf时都可以操作

[root@localhost www]# chown -R daiyan9095:daiyan9095 admin  递归更改目录文件的所有者和所有组，该文件夹及以下的文件都被更改

[root@localhost model]# pwd

[root@localhost model]# ls /  显示根目录 

[root@localhost model]# cd ~ 回到家目录

[root@localhost ~]# cd ~daiyan9095  到daiyan9095的家目录 


[root@localhost ~]# cd -   在上一个目录之间来回的切换


#8

**[root@localhost www]# cp hd.sh admin**  将hd.sh文件复制到admin，因为存在admin目录 
**
[root@localhost www]# cp hd.sh admin/a.sh** 复制文件并改名，因为不存在a.sh所以是复制文件并改名

**[root@localhost admin]# cp * mode**l 复制当前目录下的所有文件到model目录

**[root@localhost admin]# rm -rf model** 递归删除model及其下的所有文件
  
[root@localhost www]# cp index.php ~daiyan9095  复制文件到daiyan9095的家目录

[daiyan9095@localhost www]$ cd ~ 到daiyan9095的家目录

[daiyan9095@localhost ~]$ scp  远程复制

[root@localhost daiyan9095]# mv index.php index01.php  改名字

**不存在就改名，存在就是移动**

`[root@localhost daiyan9095]# mv b a`  更改目录名

`[root@localhost daiyan9095]# scp y1.php` root@www.houdunwang.com:/www/html/edu/y1.php    通过远程ssh将y1.php复制到后盾网的服务器的根目录下的www下的html下的edu的y1.php

**[root@localhost daiyan9095]# ll --full-time  显示详细的时间**

	drwx------.  4 a_1        a_1        4096 2016-06-21 17:52:48.443010831 +0800 a_1
	drwx------.  4 b          b          4096 2016-06-21 17:52:51.616010828 +0800 b
	drwx------.  4 d_1        d_1        4096 2016-06-21 21:43:53.045549143 +0800 d_

`[root@localhost daiyan9095]# touch -t 0902211033 a`  将文件a的创建时间改为09年2月21日10点33分

####软连接--快捷方式
	[daiyan9095@localhost admin]$ touch baidu.sh
	[daiyan9095@localhost admin]$ echo "echo 'baidu.sh'">>baidu.sh
	[daiyan9095@localhost admin]$ cat baidu.sh
	echo 'baidu.sh'
	[daiyan9095@localhost admin]$ ./baidu.sh
	bash: ./baidu.sh: Permission denied
	[daiyan9095@localhost admin]$ chmod u+x baidu.sh 
	[daiyan9095@localhost admin]$ ./baidu.sh
	baidu.sh


	[root@localhost admin]# ./baidu.sh   本地执行
	baidu.sh
#####创建软链接
	[root@localhost admin]# ln -s /tmp/www/admin/baidu.sh /usr/bin/baidu.sh  创建软连接，类似快捷方式
	
	[root@localhost ~]# baidu.sh   不用加路径直接执行
	baidu.sh


####`[root@localhost tmp]# ls -il`   显示文件节点/ID号 
	total 4
	927247 -rw-r--r--. 1 root   root0 Jun 17 12:57 1.txt
	927241 -rw-r--r--. 1 root   root0 Jun 17 12:14 a.sh
	927246 -rwxrw-r--. 1 daiyan9095 daiyan9095 16 Jun 17 12:46 baidu.sh
	927240 -rw-r--r--. 1 root   root0 Jun 17 12:12 hd.sh

####硬链接：多个文件名引用同一个文件
	[root@localhost admin]# ln /tmp/www/admin/1.txt /tmp/www/1.bak.txt
	
	[root@localhost www]# ll -i
	total 4
	927247 -rw-r--r--. 2 root       root          0 Jun 17 12:57 1.bak.txt  此时它与1.txt的节点号相同，且变为2表示两个引用
	927229 drwxr-xr-x. 2 daiyan9095 daiyan9095 4096 Jun 17 12:57 admin
	927239 -rw-r--r--. 1 root       root          0 Jun 17 12:12 hd.sh
	927085 -rw-r--rwx. 1 root       root          0 Jun 17 12:17 index.php


	[root@localhost admin]# rm 1.txt
	rm: remove regular empty file `1.txt'? y
	[root@localhost admin]# cd ..
	[root@localhost www]# l
	bash: l: command not found
	[root@localhost www]# ll -i
	total 4
	927247 -rw-r--r--. 1 root       root          0 Jun 17 12:57 1.bak.txt  此时仅有一个引用，变为1
	927229 drwxr-xr-x. 2 daiyan9095 daiyan9095 4096 Jun 17 13:03 admin
	927239 -rw-r--r--. 1 root       root          0 Jun 17 12:12 hd.sh
	927085 -rw-r--rwx. 1 root       root          0 Jun 17 12:17 index.php

####mv也可以移动，也可以改名

**存在就是改名，不存在或文件夹就是移动**
	
	[root@localhost www]# mv 1.bak.txt admin/1.bak.txt
	[root@localhost www]# cd admin
	[root@localhost admin]# ll
	total 4
	-rw-r--r--. 1 root       root        0 Jun 17 12:57 1.bak.txt
	-rw-r--r--. 1 root       root        0 Jun 17 12:14 a.sh
	-rwxrw-r--. 1 daiyan9095 daiyan9095 16 Jun 17 12:46 baidu.sh
	-rw-r--r--. 1 root       root        0 Jun 17 12:12 hd.sh

cat 查看文件所有内容 
more 一部分的查看文件内容 相当于分页，分屏

**[root@localhost www]# more index.php**  可以用空格键来翻页，按q则退出查看

**less index.php**  可以上下滚动的查看文件内容 相当于长网页，可以在底部运用正则表达式来高亮匹配内容

/isset   按n向下查看，按q退出

[root@localhost www]# less index.php
...
果要将一个变量强制转换为某类型(如在变量前加(string)转换为字符串)，可以对其使用强制转换或者 `settype()` 函数。
gettype()返回参数的类型字符串
echo gettype("a");//string
$a=array();
echo gettype($a);//array 

/isset   正则查询

按n向下查询，N向上查找；按q退出 

`[root@localhost www]# tail -5 index.php`   仅显示后5行
`[root@localhost www]# head -5 index.php`   仅显示前5行

查找文件
`[root@localhost www]# find / -user daiyan9095`  从根目录下开始查找与daiyan9095用户相关的文件

`[root@localhost www]# find / -size +6000k` 查找600k以上的文件

`[root@localhost www]# find / -name index.php`  查找文件名为index.php的文件

`[root@localhost www]# which passwd`  查找passwd
/usr/bin/passwd

**[root@localhost www]# whereis index.php** 查找index.php
index: /usr/share/man/man3/index.3.gz /usr/share/man/man3p/index.3p.gz
没有查找到，是因为那是今天创建的文件，文件名数据库还未更新

updatedb  更新文件名数据库
**[root@localhost www]# locate index.php**  这时查找到index.php文件
/home/daiyan9095/.index.php.swp

**which 和 whereis  一般用来查询命令**

**locate 用来查询某一文件（从数据库，此数据库一天更新一次）**

find是全盘搜索，速度较慢

	[root@localhost www]# which ll
	alias ll='ls -l --color=auto'
	      /bin/ls
	和
	[root@localhost www]# whereis ls
	ls: /bin/ls /usr/share/man/man1/ls.1.gz /usr/share/man/man1p/ls.1p.gz

**find可以根据大小、名字、时间等进行查询，查看文档**

#磁盘操作

**[root@localhost ~]#** ls -lh  h以b k M 等来显示文件的大小

**[root@localhost ~]# du -a**  查看目录大小

	[root@localhost tmp]# du -a
	4     ./pulse-niRveYndCUNc
	0     ./dy/index.php
	4     ./dy/a
	8     ./dy
	...

**[root@localhost tmp]# du -ah**  以可识别的单位来显示磁盘文件的大小

	4.0K  ./pulse-niRveYndCUNc
	0     ./dy/index.php
	4.0K  ./dy/a
	8.0K  ./dy
	4.0K  ./ks-script-2Ru861.log
	4.0K  ./virtual-
	...

以上命令显示的包括目录中的文件

**[root@localhost tmp]# du -s  列出总大小**

    
**[root@localhost tmp]# du -sh**  h是以可识别的单位表示
516K  

**[root@localhost tmp]# du -shS**   仅查看当前目录的大小，不包括子目录,其实就是将文件夹排除在外

**[root@localhost tmp]# df ** 查看分区

[root@localhost tmp]# df -h   以可识别的单位来显示分区大小

	[root@localhost tmp]# df -h
	Filesystem      Size  Used Avail Use% Mounted on
	/dev/sda2        18G  2.6G   14G  16% /
	tmpfs           491M  228K  491M   1% /dev/shm
	/dev/sda1       283M   34M  234M  13% /boot

**[root@localhost tmp]# sync**  将内存的数据同步到磁盘中，在关闭之前要多执行

**[root@localhost tmp]# fdisk -l**  查看分区结构，fdisk命令

**init 0** 和 **halt**  也可以关机

linux磁盘要**分区**然后**挂载**才能使用

**[root@bogon Desktop]# ls /dev**  查看磁盘文件夹

**[root@bogon Desktop]# fdisk /dev/sdb**    对sdb磁盘分区，一定要确定是哪块硬盘分区，以避免其他硬盘被格式化

	[root@bogon Desktop]# fdisk /dev/sdb
	Command (m for help): n   根据m提示出的帮助来操作，n为添加一个新的分区
	Command action
	   e   extended           扩展分区
	   p   primary partition (1-4)    主分区，最多只能添加4个
	
	p          添加主分区
	Partition number (1-4): 1      添加1号主分区
	First cylinder (1-391, default 1):    选择开始位置，新盘就选择默认，回车即可
	Using default value 1
	Last cylinder, +cylinders or +size{K,M,G} (1-391, default 391): +1G    选择分区大小，可以使用K M G来表示
	
	Command (m for help): n     添加第二号分区
	Command action
	   e   extended
	   p   primary partition (1-4)
	p                           添加主分区
	Partition number (1-4): 2     分区号为2,1刚才已经被占用
	First cylinder (133-391, default 133):     开始位置，选择默认即可
	Using default value 133
	Last cylinder, +cylinders or +size{K,M,G} (133-391, default 391):   选择默认大小即表示将剩下的所有分给2分区
	Using default value 391
	
	Command (m for help):  m   查看帮助
	Command (m for help): p     表示打印分区表，上一步选择m提示有此功能
	
	Disk /dev/sdb: 3221 MB, 3221225472 bytes
	255 heads, 63 sectors/track, 391 cylinders
	Units = cylinders of 16065 * 512 = 8225280 bytes
	Sector size (logical/physical): 512 bytes / 512 bytes
	I/O size (minimum/optimal): 512 bytes / 512 bytes
	Disk identifier: 0xc4a6922b

	   Device Boot      Start         End      Blocks   Id  System
	/dev/sdb1               1         132     1060258+  83  Linux    分区1
	/dev/sdb2             133         391     2080417+  83  Linux    分区2
	分区后不能使用，需要格式化(挂载)才能用（添加了文件系统）

	Command (m for help): d    删除分区
	
	Command (m for help): n
	Command action
	   e   extended
	   p   primary partition (1-4)
	e                   添加扩展分区
	Partition number (1-4): 3
	First cylinder (198-391, default 198): 
	Using default value 198
	Last cylinder, +cylinders or +size{K,M,G} (198-391, default 391): 
	Using default value 391
	
	打印分区情况
	   Device Boot      Start         End      Blocks   Id  System
	/dev/sdb1               1         132     1060258+  83  Linux
	/dev/sdb2             133         197      522112+  83  Linux
	/dev/sdb3             198         391     1558305    5  Extended

	Command (m for help): n
	Command action
	   l   logical (5 or over)            将剩余空间分给扩展分区后在分区就只能分主分区和逻辑分区
	   p   primary partition (1-4)
	
	分逻辑分区
	Command (m for help): n
	Command action
	   l   logical (5 or over)
	   p   primary partition (1-4)
	l
	First cylinder (198-391, default 198): 
	Using default value 198
	Last cylinder, +cylinders or +size{K,M,G} (198-391, default 391): +500M

	打印分区情况5和6为逻辑分区
	   Device Boot      Start         End      Blocks   Id  System
	/dev/sdb1               1         132     1060258+  83  Linux
	/dev/sdb2             133         197      522112+  83  Linux
	/dev/sdb3             198         391     1558305    5  Extended
	/dev/sdb5             198         262      522081   83  Linux
	/dev/sdb6             263         391     1036161   83  Linux

只有主分区和逻辑分区才能使用
逻辑分区从5开始，因为1-4被占位主分区

	w   write table to disk and exit
	x   extra functionality (experts only)

	Command (m for help): w    写入分区到磁盘
	The partition table has been altered!
	
	Calling ioctl() to re-read partition table.
	Syncing disks.
	
**fdisk -l  查看分区即可以看到刚才做的分区**

	   Device Boot      Start         End      Blocks   Id  System
	/dev/sdb1               1         132     1060258+  83  Linux
	/dev/sdb2             133         391     2080417+   5  Extended
	/dev/sdb5             133         197      522081   83  Linux
	/dev/sdb6             198         391     1558273+  83  Linux

**创建文件系统/格式化**

    [root@bogon Desktop]# mkfs -t ext4 /dev/sdb1   格式化sdb1分区
	-t表示要指定文件系统的类型  
	ext4指定类型

**[root@bogon Desktop]# mkfs   查看mkfs的帮助**

    Usage: mkfs [-V] [-t fstype] [fs-options] device [size]

###手动挂载
**[root@bogon Desktop]# ls /mnt/**   这个是linux通用的挂载区

**[root@bogon Desktop]# mount  查看挂载详情**

	[root@bogon Desktop]# mount
	/dev/sda2 on / type ext4 (rw)    sda2挂载了第一块硬盘的第二个分区在根目录下，所有对根目录的操作都是对这个分区的操作
	proc on /proc type proc (rw)
	sysfs on /sys type sysfs (rw)
	devpts on /dev/pts type devpts (rw,gid=5,mode=620)
	tmpfs on /dev/shm type tmpfs (rw,rootcontext="system_u:object_r:tmpfs_t:s0")
	/dev/sda1 on /boot type ext4 (rw)    同理这个挂在了boot目录下，是ext4的文件系统
	none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
	vmware-vmblock on /var/run/vmblock-fuse type fuse.vmware-vmblock (rw,nosuid,nodev,default_permissions,allow_other)

**[root@bogon ~]# mkdir /mnt/sdb1**   挂载就是创建一个目录，将分区分配到这个目录，就是将这个目录作为分区的操作空间，类似win的def盘，这个目录名随意起

**[root@bogon ~]# mount /dev/sdb1 /mnt/sdb1**    实现挂载，将sdb1分区挂载到目录sdb1

**[root@bogon ~]# cd /mnt/sdb1** 此时该分区就可以使用了，通过对这目录的操作实际就是对分区的操作
**[root@bogon sdb1]# ll**

**[root@bogon sdb1]# mount**  此时可以看到挂载了分区

**[root@bogon ~]# e2label /dev/sdb1 web**   给/dev/sdb1起一个卷标web

**[root@bogon ~]# e2label /dev/sdb1 ** 打印卷标，此时即使硬盘在电脑中随意摆放也不会乱了

**[root@bogon ~]# umount /dev/sdb1**    弹出sdb1的挂载

**[root@bogon ~]# mount**  此时在查看时就没有挂载了

**[root@bogon ~]# mount -L "web" /web **   使用卷标来挂载，使用关键字 -L 

扩展分区不用挂载

[root@bogon ~]# df -h   这里可以看到已经可用的磁盘

	[root@bogon ~]# df -h
	Filesystem      Size  Used Avail Use% Mounted on
	/dev/sda2        18G  2.6G   14G  16% /
	tmpfs           491M  248K  491M   1% /dev/shm
	/dev/sda1       283M   34M  234M  13% /boot
	/dev/sdb1       988M  1.3M  935M   1% /web

####[root@bogon ~]# df -h    全部挂载完成
	Filesystem      Size  Used Avail Use% Mounted on
	/dev/sda2        18G  2.6G   14G  16% /
	tmpfs           491M  248K  491M   1% /dev/shm
	/dev/sda1       283M   34M  234M  13% /boot
	/dev/sdb1       988M  1.3M  935M   1% /web
	/dev/sdb5       486M  2.3M  458M   1% /backup
	/dev/sdb6       1.5G  2.3M  1.4G   1% /soft

**还需要一步操作，使得电脑启动时自动挂载修改配置文件/ect/fstab,使用vim编辑即可，要小心操作**

proc                    /proc                   proc    defaults        0 0
/dev/sdb1               /web                    ext4    defaults        0 2
添加下面的一句即挂载

[root@bogon Desktop]# tail -1 /etc/fstab  查看文件内容最后一行

/dev/sdb1               /web                    ext4    defaults        0 2
/dev/sdb5               /backup                 ext4    defaults        0 0
LABEL=soft              /soft                   ext4    defaults        0 0
**上面的最后一行时以卷标形式挂载，注意卷标名唯一**


**忘记root密码就要进入单用户模式(开机时快捷键选择模式)来修改查看,单用户模式只能在服务器上操作`passwd root`输入新的密码重启即可**

然后

**mount -n -o reount,rw /**     重新挂载根目录并使其可写(在单用户只能读取文件时可以这样操作)

#12 压缩文件

体积变小  容易复制

**[root@bogon backup]# zip passwd.zip passwd**   将passwd压缩为passwd.zip，linux没有rar，因为该软件收费

**该zip压缩命令压缩文件时必须指定压缩后的文件名**

**[root@bogon www]# unzip passwd.zip**  解压缩

**[root@bogon backup]# gzip index.php**  使用gzip压缩index.php文件 

**[root@bogon backup]# gzip -d index.php.gz**  将文件解压缩

**[root@bogon backup]# bzip2 shadow**   使用bzip2压缩文件

**[root@bogon backup]# bzip2 -d shadow.bz2**   解压缩
以上方法仅能压缩单个文件


**注意：**
使用zip压缩，原文件存在于目录中，解压时原压缩文件也存在；<br/>而使用gzip压缩式，原文件消失，只保存有压缩文件，且该命令解压缩时原压缩文件不存在；<br/>bzip2的作用于用法与gzip基本相同

###tar  打包

**参数**

-    -j 使用bzip2进行打包
-    -z 使用gzip进行打包
-    -f 设置文件名
-    -c 新建打包文件
-    -v 显示执行过程
-    -x 解包
-    -t 查看压缩包内的内容，不会解包

**[root@bogon www]# tar -zcvf admin.gz admin**  将文件夹打包，使用gzip,新建打包文件，命名打包文件，显示打包过程

**[root@bogon test]# tar -zxvf /tmp/www/admin.gz **  x 是解包

**[root@bogon www]# tar -ztvf admin.gz**  查看压缩包内的内容 

	[root@bogon www]# tar -ztvf admin.gz
	-rw-r--r--. 1 root root 7947148 Jun 17 20:06 daiyan9095.tar.bz2
	drwxr-xr-x. 3 root root    4096 Jun 17 20:07 home
	-rw-r--r--. 1 root root       0 Jun 17 19:39 index.php
	-rw-r--r--. 1 root root    1441 Jun 17 19:28 passwd
	-rw-r--r--. 1 root root     753 Jun 17 19:30 passwd.zip
	----------. 1 root root     827 Jun 17 19:44 shadow

	[root@bogon backup]# cd home
	[root@bogon home]# ll
	total 4
	drwx------. 30 daiyan9095 daiyan9095 4096 Jun 17 19:15 daiyan9095

**tar解压缩并不会删除压缩包，它这点与zip相似**

##vim

i插入模式，可以更改写入

esc键为返回一般模式

退出：
: 命令模式
q 直接退出
w 保存写入的信息

在vim编辑器内发出命令:set nu  显示行号,:set nonu 不显示行号

	1 <?php
	2 class IndexControl extends Control{
	3         function index(){
	4 
	5	 }
	6 }
	7 ?>


在普通模式下快速移动，**并立即切换到编辑模式**

- i  在当前位置插入
- I  在行首插入
- a  下一个字符
- A  行尾插入
- o  下一行
- O  上一行 

**在编辑模式下执行命令**

:sh执行命令，将vim放入后台 

exit后退回到vim编辑器

	:w!强制保存
	:q!强制退出
	:w user.control.class.php  另存为user.control.class.php 
	x 删除一个字符
 
:set tapstop=2 设置tab空格为两个字符

:2 跳转到第二行

:100 跳转到100行

:0  调到最开始

:20000很大的数字则调到最后

:/查找内容   向下查找

   :n 和:N来向下和向上查找

:?查找内容 向上查找
                                                                        
:1,10s/e/p/g  从第一行到10行替换(s)，将e换为p，g表示执行全部替换

在退出边界模式下直接按u是撤销的意思

:1,10s/e/p/gc  每次替换都需要确定，以免出错

**粘贴和复制**

dd剪切当前行

yy复制

p是粘贴到当前光标下一行

P粘贴到上一行

按出12 然后按dd则从当前光标及之下的12行被剪切

按出3，然后按yy则复制当前光标及之下的3行

**:r IndexCtrol.class.php**  导入另一个文件中的数据

:sp  打开一个新的空窗口

:wq!强制关闭一个窗口

**:sp IndexControl.class.php 在新的窗口中打开IndexControl.class.php**

ctrl+ww在多个窗口之间进行切换

**:set autoindent 设置自动缩进，以上操作仅影响到当前的文件**

要想影响到所有的文件，在用户家目录下，建立新的文件.vimrc,编辑内容
set nu
set autoindent
set tabstop=2
保存退出
这时用vim打开任何文件都带有了配置


#17 

**/etc/passwd文件**
daiyan9095:x:500:500:centos:/home/daiyan9095:/bin/bash
用户名   x代表密码 500为id 500为组的id home/daiyan9095为家目录  

**创建账号bjhd**

    [root@bogon backup]# useradd bjhd

**查看/etc/passwd的最后一行**

[root@bogon backup]# tail -1 /etc/passwd
bjhd:x:501:501::/home/bjhd:/bin/bash

这个文件中的字段用:隔开

**现在的用户密码不存在passwd里了**，而是存在了/etc/shadow中

[root@bogon backup]# tail -1 /etc/shadow
bjhd:!!:16970:0:99999:7:::

**为用户bjhd添加密码admin888**

	[root@bogon backup]# passwd bjhd
	Changing password for user bjhd.
	New password: 
	BAD PASSWORD: it is based on a dictionary word
	Retype new password: 
	passwd: all authentication tokens updated successfully.

此时密码做了更改：

	[root@bogon backup]# tail -1 /etc/shadow
	bjhd:$1$UlfrA.xc$30M5ZIl5fWJxX84/D8k.W0:16970:0:99999:7:::

- 16970表示设置密码的事件unix的天数，
- 0表示随时可以再更改密码需要的时间，若为2表示需要2天后才能更改密码，当然root不受此限制
- 99999表示99999天后必须修改密码，否则登录不了
- 7表示到期前7天会提醒用户修改密码
- 后面的参数设置即使过期了也可以在指定天数内修改，否则过了期就不能再修改密码了


#用户高级管理
**[root@bogon backup]# more /etc/group**  查看管理用户组的文件

	daiyan9095:x:500:
	bjhd:x:501:

第一个参数为组名，第二个参数为组密码 第三个参数501为组id
如果还有参数则是组的成员
初始组及用户即为一个组则不显示

**[root@bogon backup]# more /etc/gshadow**   查看组的密码

	daiyan9095:!::
	bjhd:!::

！表示没有密码
第一个参数为组名，第二个参数为组的密码，第三个参数为组的管理员，第四个参数为组的成员

**[root@bogon backup]# ls /home**
bjhd  daiyan9095   添加完用户后会在home下自动创建这个用户的家目录

	[root@bogon backup]# useradd u1
	[root@bogon backup]# ls /home
	bjhd  daiyan9095  u1

**u1:x:502:502::/home/u1:/bin/bash **  同时在passwd文件中添加了用户的信息

	cat /etc/group  下也会创建组
	bjhd:x:501:
	u1:x:502:

**[root@bogon backup]# groupadd hd**  创建一个hd的组

	cat /etc/group   查看新建的组
	u1:x:502:
	hd:x:503:

**[root@bogon backup]# useradd -g hd u2**  新添加一个用户u2并指定组为hd

	[root@bogon backup]# tail -2 /etc/passwd
	u1:x:502:502::/home/u1:/bin/bash
	u2:x:504:503::/home/u2:/bin/bash
	[root@bogon backup]# tail -1 /etc/group
	hd:x:503:

**[root@bogon backup]# usermod -G hd xiaobai**  **添加**附加组，这时小白属于自己的组和hd组

**注意：在添加用户时指定组用-g，而在为已存在的用户添加组时用-G**

	[root@bogon backup]# id xiaobai  查看小白用户的id
	uid=504(xiaobai) gid=504(xiaobai) groups=504(xiaobai),503(hd)
	可以看到小白的组属于自己和hd

**更改文件的组：chgrp**


	[root@bogon test]# chgrp hd hd1  更改hd1的用户组为hd
	[root@bogon test]# ll
	total 12
	drwxr-xr-x. 2 daiyan9095 daiyan9095 4096 Jun 17 13:05 admin
	drwxr-sr-x. 2 root       hd         4096 Jun 17 23:44 hd  此时组变为hd
	-rw-r--r-x. 1 root       root         64 Jun 17 21:17 index.php

**更改文件的所有者和所有组**
	
	[root@bogon test]# chown root:root hd  改变index.php的所有者和所有组 

chgrp hd hdddd  仅改变所有组为hd
	
	[root@bogon test]# chmod g+w hd  为hd的所有组添加w权限
	
	
	[xiaobai@bogon test]$ cd hd  此时xiaobai可以在hd下创建文件
	[xiaobai@bogon hd]$ ll
	total 0
	-rw-rw-r--. 1 xiaobai hd 0 Jun 17 23:52 hdphp
	[xiaobai@bogon hd]$ touch dd
	
	[u1@bogon test]$ cd hd   u1就创建不了，没有操作的权限
	[u1@bogon hd]$ touch hehe
	touch: cannot touch `hehe': Permission denied
	
[root@bogon hd]# useradd -G hd,u1 h6 创建新的用户u6并**添加多个附加组**

	[root@bogon hd]# id h6
	uid=505(h6) gid=505(h6) groups=505(h6),502(u1),503(hd)
	
	[root@bogon hd]# useradd -M u7  创建u7但不创建家目录
	[root@bogon hd]# ls /home
	bjhd  daiyan9095  h6  u1  u2  xiaobai

##修改用户的信息

[root@bogon hd]# usermod -G hd h6  修改h6的组为hd和自身
[root@bogon hd]# id h6
uid=505(h6) gid=505(h6) groups=505(h6),503(hd)

**[root@bogon hd]# usermod -L h6**   锁定用户

此时/etc/shadow下的对应行密码前多了一个！
h6:!$1$SNnLzR.X$v6/epl4dsDuarfoakGwcx0:16970:0:99999:7:::

**[root@bogon hd]# usermod -U h6  为用户解锁**

此时相应的!也没了
h6:$1$SNnLzR.X$v6/epl4dsDuarfoakGwcx0:16970:0:99999:7:::

**注意：用户锁定后就不能登陆了**

###删除用户
[root@bogon hd]# userdel u1
[root@bogon hd]# ls /home  但是该用户在home下的文件没有删除
bjhd  daiyan9095  h6  u1  u2  xiaobai

[root@bogon hd]# userdel -r u2  此时连同家目录一起删除
[root@bogon hd]# ls /home
bjhd  daiyan9095  h6  u1  xiaobai

###删除没有所有者的目录
	[root@bogon hd]# find / -nouser  全盘搜索没有所有者的文件
	
	[root@bogon hd]# find / -nouser -exec rm -rf {} \; 查找并执行删除操作
	
	[root@bogon hd]# find / -nouser -exec rm -ri {} \;  连续确定是否删除
	{}就代表找到的文件

root可以更改任何用户的密码 

其他用户只能更改自己的密码

**[root@bogon hd]# passwd -l bjhd**  也可以用来锁定用户
此时在shadow密码前加两个!!

**另一用户锁定 usermod -L bjhd**

**[root@bogon hd]# passwd -u bjhd**  解除锁定

**[root@bogon hd]# passwd -S bjhd  查看状态**
bjhd PS 2016-06-17 0 99999 7 -1 (Password set, MD5 crypt.)

###修改用户信息
chage -l 用户名

	[root@bogon hd]# chage -l bjhd
	Last password change                            : Jun 18, 2016
	Password expires                          : never
	Password inactive                         : never
	Account expires                                 : never
	Minimum number of days between password change        : 0
	Maximum number of days between password change        : 99999
	Number of days of warning before password expires     : 7


	[root@bogon hd]# chage -m 3 bjhd  修改了需要3天后才可以修改密码
	[root@bogon hd]# chage -l bjhd
	Last password change                            : Jun 18, 2016
	Password expires                          : never
	Password inactive                         : never
	Account expires                                 : never
	Minimum number of days between password change        : 3
	Maximum number of days between password change        : 99999
	Number of days of warning before password expires     : 7
	
	[root@bogon hd]# chage -M 10 bjhd 设置10天后必须修改密码
	[root@bogon hd]# chage -l bjhd
	Last password change                            : Jun 18, 2016
	Password expires                          : Jun 28, 2016
	Password inactive                         : never
	Account expires                                 : never
	Minimum number of days between password change        : 3
	Maximum number of days between password change        : 10
	Number of days of warning before password expires     : 7
	
	[root@bogon hd]# chage -W 9 bjhd  将要修改9天之前必须提醒我
	[root@bogon hd]# chage -l bjhd
	Last password change                            : Jun 18, 2016
	Password expires                          : Jun 28, 2016
	Password inactive                         : never
	Account expires                                 : never
	Minimum number of days between password change        : 3
	Maximum number of days between password change        : 10
	Number of days of warning before password expires     : 9

#18 

[root@bogon test]# chmod 0777 index.php  更改文件的权限
**0777中的0代表特殊权限位**

[root@bogon test]# passwd --help 查看某个命令的帮助

[root@bogon test]# man passwd  查询更加详细的帮助信息

**查看passwd命令所在的位置，which whereis  find也可以  locate**
	
	[root@bogon test]# which passwd
	/usr/bin/passwd
	[root@bogon test]# whereis passwd  
	passwd: /usr/bin/passwd /etc/passwd /etc/passwd.OLD /usr/share/man/man5/passwd.5.gz /usr/share/man/man1/passwd.1.gz

**which 和 whereis 专门找命令地址的，locate则一般用来寻找某一文件**


	[root@bogon test]# ls -l /usr/bin/passwd 
	-rwsr-xr-x. 1 root root 30768 Nov 23  2015 /usr/bin/passwd

**这个命令文件是rws，s代表拥有`suid`的权限位，这个s使得当其他用户拥有*执行*权限即x时，在执行该文件时会临时转换为root执行命令**


[root@bogon test]# ls -l /etc/shadow
----------. 1 root root 938 Jun 18 00:50 /etc/shadow
密码文件其他任何用户没有权限操作，只有root能改

chmod 4755 index.php  将index.php的权限改为 
-rwsr-xr-x  这里的index.php**必须是可执行文件不能是目录**，而且要有操作该文件的权限

**为文件所有者增加s属性**

	[root@bogon test]# chmod 4755 index.php
	[root@bogon test]# ll
	total 12
	drwxr-xr-x. 2 daiyan9095 daiyan9095 4096 Jun 17 13:05 admin
	drwxrwsr-x. 2 root       hd         4096 Jun 17 23:55 hd
	-rwsr-xr-x. 1 root       root         84 Jun 18 02:10 index.php

**为文件所有组增加s属性**

sgid 当执行文件时变为文件的所有者，类似suid,可以对目录操作

	[root@bogon test]# chmod 2755 hd
	[root@bogon test]# ll
	total 12
	drwxr-xr-x. 2 daiyan9095 daiyan9095 4096 Jun 17 13:05 admin
	drwxr-sr-x. 2 root       hd         4096 Jun 17 23:55 hd
	-rwxr-xr-x. 1 root       root         84 Jun 18 02:10 index.php

也可以单独设置：
 ` chmod g+s hd`
表示当我在整个文件夹下操作时临时自动变为hd组

**2770的2代表sgid**,而
**4755的4代表suid**
当这样设置时，其他用户要有x权限才能临时转换为对应用户或组


[xiaobai@bogon hd]$ touch hh  #小白用户创建文件hh

	[xiaobai@bogon hd]$ ll
	total 0
	-rw-rw-r--. 1 xiaobai hd 0 Jun 17 23:55 dd
	-rw-rw-r--. 1 xiaobai hd 0 Jun 17 23:52 hdphp
	-rw-rw-r--. 1 xiaobai hd 0 Jun 18 02:27 hh  
这时虽然是xiaobai创建的文件，**但是组却会变为hd**，注意xiaobai要有x权限

**[root@bogon hd]# groupadd blog**  增加blog组

**chgrp是更改用户组**

	[root@bogon test]# chgrp blog Application/
	[root@bogon test]# ll
	total 16
	drwxr-xr-x. 2 daiyan9095 daiyan9095 4096 Jun 17 13:05 admin
	drwxr-sr-x. 2 root       blog       4096 Jun 18 02:31 Application
	drwxrwsrwx. 2 root       hd         4096 Jun 18 02:27 hd
	-rwxr-xr-x. 1 root       root         84 Jun 18 02:10 index.php

添加用户，删除用户及其文件，为用户添加附加组
	
	[root@bogon test]# useradd liu
	[root@bogon test]# useradd li
	[root@bogon test]# useradd wnag
	[root@bogon test]# userdel -r wnag
	[root@bogon test]# ls /home
	bjhd  daiyan9095  li  liu  xiaobai
	[root@bogon test]# useradd wang
	[root@bogon test]# usermod -G blog liu
	[root@bogon test]# id liu
	uid=507(liu) gid=508(liu) groups=508(liu),507(blog)


**[root@bogon test]# usermod -G blog wang**  这个命令是附加组，原有组不变 

**chgrp是修改文件的组，不能用来修改用户的组**

	[liu@bogon Application]$ touch liu.html
	[liu@bogon Application]$ ll
	total 0
	-rw-rw-r--. 1 liu blog 0 Jun 18 02:58 liu.html  此时的liu.html文件自动变为blog组
	[liu@bogon Application]$ 


[li@bogon Application]$ vim liu.html   属于一个组的用户可以修改组文件


**-rw-rw-r-t如果目录设置了t**，则所有在**该目录**之下的文件只能被创建者删除，其他用户不能删除

**注意：这个权限要加载目录上**

	drwxr-xr-x. 2 root       root       4096 Jun 18 03:10 sbit
	[root@bogon test]# chmod 1777 sbit  设置t属性
	drwxrwxrwt. 2 root       root       4096 Jun 18 03:10 sbit

**1777中的1代表sbit**，目录下的文件只能被创建者删除（不考虑root）
也可以chmod o+t sbit 

	drwxrwxrwt. 2 root       root       4096 Jun 18 03:10 sbit
	-rwxrwxrwx. 1 liu liu 29 Jun 18 03:15 liu.css
	[li@bogon sbit]$ rm liu.css  即使对该目录有w权限，但是不能删除
	rm: cannot remove `liu.css': Operation not permitted
	
	[root@bogon sbit]# su liu 
	[liu@bogon sbit]$ rm liu.css 只能由创建者删除

**能不能删文件要看对目录的是否有w权限和是否设置了t属性**


##ACL 
这是对某个用户设置对某一文件的特殊权限

**[root@bogon test]# setfacl -m u:liu:rwx acl  设置acl,使得li对acl文件目录rwx**

	[root@bogon test]# getfacl acl
	# file: acl
	# owner: li
	# group: li
	user::rwx
	user:liu:rwx  这就是增加的权限，即授予某个用户的特殊权限
	group::r-x
	mask::rwx
	other::r-x

**对目录设置的化其中的其他用户创建的文件不会随着更改**

	[root@bogon test]# getfacl admin
	# file: admin
	# owner: daiyan9095
	# group: daiyan9095
	user::rwx
	group::r-x
	other::r-x

###给指定组设置特殊权限

	[root@bogon test]# getfacl acl
	# file: acl
	# owner: li
	# group: li
	user::rwx
	user:liu:rwx
	group::r-x
	group:blog:rwx
	mask::rwx
	other::r-x

以上的acl设置要受到mask这个值得影响
[root@bogon test]# setfacl -m m:rwx acl  设置mask的权限


#19 

`su -` 也是切换到root，这时同时改变了环境变量

`sudo` 临时切换用户并执行命令

[root@bogon root]$ vim /etc/sudoers  设置sudo需要修改该文件
在这个文件中配置文件，赋予其他用户某些root功能


##锁定用户的方法：
1. passwd -l 
2. usermod -L 
3. 修改/etc/shadow 下的密码加上!

halt也是关机 init 0  shutdown -h now

推荐使用visudo修改/etc/sudoers文件,因为如有错误会提示

     90 ## Allow root to run any commands anywhere
     91 root  ALL=(ALL)   ALL
     92 daiyan9095 ALL=(ALL) ALL  加上这一行表示从任何位置登陆的daiyan9095账号，可以却换为任何用户，可以执行任何操作；这三个属性分别对应三个all

**ctrl+shift+t 打开新的标签**

[daiyan9095@bogon ~]$ vim /etc/shadow  这样查看没有权限

[daiyan9095@bogon ~]$ sudo vim /etc/shadow  这样就能查看了

此时只要在命令最前方加上sudo则daiyan9095账号几乎与root的权限一样了

	[daiyan9095@bogon ~]$ useradd a2
	bash: /usr/sbin/useradd: Permission denied
	[daiyan9095@bogon ~]$ sudo useradd a2
	[daiyan9095@bogon ~]$ tail -1 /etc/passwd
	a2:x:510:511::/home/a2:/bin/bash
	[daiyan9095@bogon ~]$ userdel a2
	bash: /usr/sbin/userdel: Permission denied
	[daiyan9095@bogon ~]$ sudo userdel -r a2
	[daiyan9095@bogon ~]$ ls /home
	bjhd  daiyan9095  li  liu  wang  xiaobai
	
	[daiyan9095@bogon ~]$ sudo -u xiaobai ls /home  切换为xiaobai账号执行某一命令
	
	[daiyan9095@bogon ~]$ sudo -u root ls ~

ctrl+pageup/pagedown 切换标签


**`:!which cat` 编辑状态下临时执行一条命令**，`:sh` 是退出当前编辑到命令行执行命令，将编辑放在后台，然后exit返回编辑

91 root  ALL=(ALL)   ALL
92 daiyan9095 ALL=(root)   /bin/cat /etc/shadow
增加92行使得从任何途径（网络远程，本地）的daiyan9095账号都可以却换到root账号，只能执行root的cat 查看/etc/shadow文件

    [daiyan9095@bogon home]$ sudo useradd a7
    Sorry, user daiyan9095 is not allowed to execute '/usr/sbin/useradd a7' as root on bogon.
    此时的daiyan9095已经不能执行此条命令了

    [daiyan9095@bogon home]$ cat /etc/shadow
    cat: /etc/shadow: Permission denied
    [daiyan9095@bogon home]$ sudo cat /etc/shadow
    只能通过sudo查看/etc/shadow文件
    
92 daiyan9095 ALL=(root)   /bin/cat /etc/shadow,/sbin/shutdown -h now
一次添加多个命令，命令要用绝对路径。**使用which 命令名 查看命令的绝对路径**

添加sudo权限

    /usr/sbin/useradd
    92 hd_stu_1 ALL=(root)   /usr/sbin/useradd
    给hd_stu_1赋予添加用户命令
    [root@bogon ~]# id zxg
    uid=511(zxg) gid=512(zxg) groups=512(zxg)

    [root@bogon ~]# id hd_stu_1
    uid=510(hd_stu_1) gid=511(hd_stu_1) groups=511(hd_stu_1)

**编辑sudo文件用visudo,因为这个有错误提示**

**passwd可以读取而shadow不能随意读取**

	91 root  ALL=(ALL)   ALL
	92 #hd_stu_1 ALL=(root)    /usr/sbin/useradd,!/usr/bin/passwd,/usr/bin/pass    wd [a-zA-Z]*,!/usr/bin/passwd root

！表示不能执行某命令，可以使用正则表达式来匹配
加上该项!/usr/bin/passwd是因为sudo passwd 默认切换为root的密码更改


	91 Cmnd_Alias MODIFYUSERPASSWD = /sbin/shutdown -h now,!/usr/bin/passwd,/us
	        r/bin/passwd [a-zA-Z]*,!/usr/bin/passwd root
	92 root  ALL=(ALL)   ALL
	93 hd_stu_1 ALL=(root)   MODIFYUSERPASSWD

**通过别名设置`hd_stu_1`的sudo权限，这时仍可以执行**

	[hd_stu_1@bogon Desktop]$ passwd liu
	passwd: Only root can specify a user name.
	[hd_stu_1@bogon Desktop]$ sudo passwd liu
	[sudo] password for hd_stu_1: 
	Changing password for user liu.
	New password: 
	BAD PASSWORD: it is based on a dictionary word
	Retype new password: 
	passwd: all authentication tokens updated successfully.
	[hd_stu_1@bogon Desktop]$ sudo passwd root
	Sorry, user hd_stu_1 is not allowed to execute '/usr/bin/passwd root' as root on bogon.
	[hd_stu_1@bogon Desktop]$ sudo passwd
	Sorry, user hd_stu_1 is not allowed to execute '/usr/bin/passwd' as root on bogon.


还可以将多个用户存入一个别名，给这个别名设置sudo权限

     91 User_Alias ADMIN = cl_zhangsan,cl_lisi,hd_stu_1
     92 Cmnd_Alias MODIFYUSERPASSWD = /sbin/shutdown -h now,!/usr/bin/passwd,/us  r/bin/passwd [a-zA-Z]*,!/usr/bin/passwd root 
     93 root  ALL=(ALL)   ALL
     94 ADMIN=(root)    MODIFYUSERPASSWD

- 将用户`cl_zhangsan,cl_lisi,hd_stu_1`存入别名ADMIN要大写别名
- 然后设置命令的别名
- 然后设置sudo权限

		[root@bogon Desktop]# visudo
		[root@bogon Desktop]# su hd_stu_1
		[hd_stu_1@bogon Desktop]$ passwd cl_zhangsan
		passwd: Only root can specify a user name.
		[hd_stu_1@bogon Desktop]$ sudo passwd cl_zhangsan
		[sudo] password for hd_stu_1: 
		Changing password for user cl_zhangsan.
		New password: 
		BAD PASSWORD: it is based on a dictionary word
		Retype new password: 
		passwd: all authentication tokens updated successfully.

利用张三的改李四的

	[hd_stu_1@bogon Desktop]$ su cl_zhangsan
	Password: 
	[cl_zhangsan@bogon Desktop]$ passwd cl_lisi
	passwd: Only root can specify a user name.
	[cl_zhangsan@bogon Desktop]$ sudo passwd cl_lisi
	
	We trust you have received the usual lecture from the local System Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

	[sudo] password for cl_zhangsan: 
	Changing password for user cl_lisi.
	New password: 
	BAD PASSWORD: it is based on a dictionary word
	Retype new password: 
	passwd: all authentication tokens updated successfully.

#20 
##加入到组,设置组的特殊权限

	[root@bogon ~]# groupadd banzhang
	[root@bogon ~]# usermod -G banzhang liu
	[root@bogon ~]# id liu
	uid=507(liu) gid=508(liu) groups=508(liu),515(banzhang)
	[root@bogon ~]# usermod -G banzhang wang
	[root@bogon ~]# id wang
	uid=509(wang) gid=510(wang) groups=510(wang),515(banzhang)

增加了组的sudo,liu属于组

	[root@bogon ~]# su liu
	[liu@bogon root]$ passwd zxg
	passwd: Only root can specify a user name.
	[liu@bogon root]$ sudo passwd zxg        使用sudo
	[sudo] password for liu: 
	Changing password for user zxg.
	New password: 
	BAD PASSWORD: it is based on a dictionary word
	Retype new password: 
	passwd: all authentication tokens updated successfully.
	[liu@bogon root]$ exit
	exit
	[root@bogon ~]# su zxg
	[zxg@bogon root]$ sudo passwd liu
	
	We trust you have received the usual lecture from the local System
	Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

	[sudo] password for zxg: 
	Sorry, try again.
	[sudo] password for zxg:   
	zxg is not in the sudoers file.  This incident will be reported.   zxg不在此组里，不能用sudo


一个账号可以从多个位置同时登陆

**w**

	[zxg@bogon root]$ w  显示当前登录的账号
	 16:51:08 up 13 min,  3 users,  load average: 0.11, 0.42, 0.37
	USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
	daiyan90 tty1     :0               16:38   13:15   8.52s  0.33s pam: gdm-passwo
	daiyan90 pts/0    :0.0             16:39    1.00s  0.33s  2.74s /usr/bin/gnome-
	daiyan90 pts/1    :0.0             16:49    1:09   0.00s  0.00s bash

- 16:51:08  为当前的时间
- up 13 min  为运行了多长时间
- 3 users  当前在线的账户数
- load average: 0.11, 0.42, 0.37  为CPU的负载，分别为1分钟、5分钟和15分钟的负载，当为1时说明是满负荷，若是两个cpu则为2时满负荷

- USER  为用户 
- TTY   为终端
- FROM  为从哪里登录
- LOGIN 为登录的时间
- IDLE  为空闲多长时间
- JCPU  为账户运行时占用cpu的时间
- PCPU  为当前执行命令所占cpu时间
- WHAT  为当前执行的命令   此处为w

**who**

	[zxg@bogon root]$ who   查看当前用户、登录时间和终端，w的简洁显示
	daiyan9095 tty1         2016-06-18 16:38 (:0)
	daiyan9095 pts/0        2016-06-18 16:39 (:0.0)
	daiyan9095 pts/1        2016-06-18 16:49 (:0.0)


[root@bogon ~]# who am i  查看自己
daiyan9095 pts/0        2016-06-18 16:39 (:0.0)

**剔除指定用户**

	[daiyan9095@bogon Desktop]$ pkill -kill -t pts/1  剔除当期用户，pts/1为该用户的终端



**[daiyan9095@bogon Desktop]$ last   查看过去登录的账号信息**
	
	daiyan90 pts/1        :0.0             Sat Jun 18 16:49   still logged in   
	daiyan90 pts/0        :0.0             Sat Jun 18 16:39 - 17:07  (00:28)    
	daiyan90 tty1         :0               Sat Jun 18 16:38   still logged in   
	reboot   system boot  2.6.32-642.el6.x Sat Jun 18 16:38 - 17:10  (00:32)    
	daiyan90 pts/0        :0.0             Sat Jun 18 06:09 - down   (00:32)    
	daiyan90 pts/0        :0.0             Sat Jun 18 05:21 - 06:09  (00:47)    
	daiyan90 tty1         :0               Sat Jun 18 05:20 - down   (01:21)    
	reboot   system boot  2.6.32-642.el6.x Sat Jun 18 05:19 - 06:42  (01:22)    
	daiyan90 pts/1        :0.0             Sat Jun 18 04:37 - down   (00:23)    
	daiyan90 pts/0        :0.0             Sat Jun 18 04:32 - down   (00:28)    
	daiyan90 pts/1        :0.0             Sat Jun 18 04:17 - 04:32  (00:14)  


**[daiyan9095@bogon Desktop]$ lastlog 查看每一个用户最后登录的时间**

	Username         Port     From             Latest
	root                                       **Never logged in**
	bin                                        **Never logged in**  bin/lp等是系统账
	号，不能登录，查看cat /etc/passwd 也可以看到自后的nologin
	daemon                                     **Never logged in**
	adm                                        **Never logged in**
	lp                                         **Never logged in**
	sync                                       **Never logged in**
	shutdown                                   **Never logged in**
	halt                                       **Never logged in**
	bjhd                                       **Never logged in**
	xiaobai                                    **Never logged in**
	u7                                         **Never logged in**
	liu              tty2                      Sat Jun 18 17:15:45 -0700 2016
	hd_stu_1                                   **Never logged in**
	zxg                                        **Never logged in**
	cl_zhangsan                                **Never logged in**



如，即使这些账号有密码也不能登录，因为nologin是没有终端界面

	pulse:x:497:496:PulseAudio System Daemon:/var/run/pulse:/sbin/nologin
	sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin


**关机并且发送关闭广播**

	[root@bogon ~]# shutdown -h +3 "will shutdown"
	
	Broadcast message from daiyan9095@bogon
	   (/dev/pts/1) at 17:20 ...
	
	The system is going down for halt in 3 minutes!

**向某个登录账号发送信息**

	[root@bogon ~]# write daiyan9095  pts/0   向daiyan9095在端口pts/0的账号发送信息
	hello    信息为hello
	[root@bogon ~]#     按ctrl+d回到命令行


**向所有用户发送信息，即广播**

	[root@bogon ~]# wall "system will shutdown"   信息为system will shutdown
	[root@bogon ~]# 
	Broadcast message from root@bogon (pts/1) (Sat Jun 18 17:24:56 2016):
	
	system will shutdown
	[daiyan9095@bogon Desktop]$     按ctrl+d回到命令行


gcc编译软件，编译c语言编写的                   <br/>
ls passwd mkdir都是可执行文件                 <br/>
源代码--》编译后--》执行程序


1. [root@bogon www]# ./configure gcc    检测gcc编译环境，依赖函数库是否已经安装
2. 当configure检测通过后，会生成makefile文件
3. make 根据makefile生成可执行文件(二进制文件)
4. make install 将文件安装到各目录

linux:默认配置文件放在/etc下                          <br/>
软件安装生成的函数库放在/lib下或者/usr/lib            <br/>
生成的数据库放在/var/lib下                           <br/>
软件的可执行文件一般放在/usr/local下或/usr/local/bin下


[root@bogon www]# echo $PATH
/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/daiyan9095/bin

**安装的文件需要设置软连接否则要打绝对路径名才能执行**

**函数库：**

      静态函数库
      动态函数库 当程序运行，需要函数功能-》执行函数库

##安装软件

**下载压缩包-解压-检测环境-make-make install**

[root@bogon ~]# dhclient    动态获得一个IP

	[root@bogon ~]# dhclient
	[root@bogon ~]# ping www.baidu.com
	PING www.a.shifen.com (220.181.111.188) 56(84) bytes of data.
	64 bytes from 220.181.111.188: icmp_seq=1 ttl=128 time=3.68 ms
	64 bytes from 220.181.111.188: icmp_seq=2 ttl=128 time=4.37 ms
	说明网络连接成功


memcache软件 --做缓存，内存的缓存，用内存来临时存储数据，加快速度

wget  --下载 支持http和ftp

**[root@bogon ~]# wget http://www.memcached.org/files/memcached-1.4.26.tar.gz   下载软件压缩包**

	[root@bogon mysql]# wget www.memcached.org/files/memcached-1.4.26.tar.gz
	--2016-06-18 18:28:49--  http://www.memcached.org/files/memcached-1.4.26.tar.gz
	Resolving www.memcached.org... 173.255.253.96
	Connecting to www.memcached.org|173.255.253.96|:80... connected.
	HTTP request sent, awaiting response... 200 OK
	Length: 373384 (365K) [application/x-tar]
	Saving to: “memcached-1.4.26.tar.gz”
	
	100%[======================================>] 373,384      424K/s   in 0.9s    
	
	2016-06-18 18:28:50 (424 KB/s) - “memcached-1.4.26.tar.gz” saved [373384/373384]
	
	-rw-r--r--. 1 root root 373384 Jun 17 13:24 memcached-1.4.26.tar.gz

----------

	[root@bogon mysql]# mv memcached-1.4.26.tar.gz /usr/local/src   移动源码包到/usr/local/src里
	[root@bogon mysql]# cd /usr/local/src
	[root@bogon src]# ll
	total 368
	-rw-r--r--. 1 root root 373384 Jun 17 13:24 memcached-1.4.26.tar.gz


	[root@bogon src]# tar -zxvf memcached-1.4.26.tar.gz   解压缩

**进入解压目录查看是否存在configure文件**

	config.h.in   LICENSE.bipbuffer  README.md           util.c
	config.sub    logger.c           sasl_defs.c         util.h
	configure     logger.h           sasl_defs.h         version.m4
	configure.ac  m4                 scripts
	看到了configure文件，执行这个文件，检测环境
	[root@bogon memcached-1.4.26]# ./configure 
	出现错误，如果现实没有安装gcc
	如果没有安装gcc,则安装gcc
	yum install gcc  一路按y
	或者 yum -y install gcc 

**安装软件解包后要先执行confgure来看环境、创建环境，出错就解决**

**config.status: creating test/Makefile  只要出现makefile说明该软件安装环境全部满足**

[root@bogon libevent-2.0.22-stable]# ls   此时查看会看到makefile文件
	aclocal.m4              evdns.h                 libevent.pc.in
	arc4random.c            event.c                 libevent_pthreads.pc
	autogen.sh              event.h                 libevent_pthreads.pc.in
	buffer.c                event-internal.h        libtool
	bufferevent_async.c     event_iocp.c            LICENSE
	bufferevent.c           event_rpcgen.py         listener.c
	bufferevent_filter.c    event_tagging.c         log.c
	bufferevent-internal.h  evhttp.h                log-internal.h
	bufferevent_openssl.c   evmap.c                 ltmain.sh
	bufferevent_pair.c      evmap-internal.h        m4
	bufferevent_ratelim.c   evport.c                make-event-config.sed
	bufferevent_sock.c      evrpc.c                 Makefile

**[root@bogon libevent-2.0.22-stable]# make  然后当前目录下执行make生成可执行文件即编译**

**[root@bogon libevent-2.0.22-stable]# make install  然后把配置文件可执行文件和帮助文件等安装到各个目录中**

**流程：**

下载软件压缩包                 <br/>
|                         <br/>
在指定的文件目录解压                   <br/>
|                                     <br/>
进入到解压目录执行./configure 文件                       <br/>
|                                        <br/>
出错就在安装需要的文件，直至看到makefile说明环境满足                    <br/>
|                                      <br/>
然后make 生成可执行文件                         <br/>
|                                             <br/>
然后make install将生成的配置文件帮助文档等等放到各个目录中              <br/>

安装软件最好切换到root下或者sudo 因为可能要写入某些文件如 /usr/sbin 

make && make install  可以自动在make执行完后执行make install 


[root@bogon memcached-1.4.26]# ./configure --help   可以查看安装的帮助文档，包括安装完后各个文件放在那里

	Installation directories:
	  --prefix=PREFIX         install architecture-independent files in PREFIX
	                          [/usr/local]  这一项指定安装到的文件夹

**可以利用参数指定安装到哪里**

	[root@bogon memcached-1.4.26]# ./configure --prefix=/usr/local/memcache   指定安装目录

**[root@bogon memcached-1.4.26]# make clean   之前安装过一次，再次安装时清除之前生成的编译文件**

**[root@bogon memcached-1.4.26]# make && make install   然后重新编译 分配文件**

**或者直接 make clean  && make && make instal   也不用管之前是否编译过也可以用make clean**

**这样过之后再指定安装目录处安装了文件**

	[root@bogon local]# ls
	bin  etc  games  include  lib  lib64  libexec  memcache  sbin  share  src
	[root@bogon local]# cd memcache/
	[root@bogon memcache]# ls
	bin  include  share
	[root@bogon memcache]# cd bin
	[root@bogon bin]# ls
	memcached
	[root@bogon bin]# cd memcached 

**[root@bogon local]# memcache  因为没有配置环境变量且不是绝对路径**
bash: memcache: command not found


[root@bogon bin]# ./memcached   这时仍会出错是因为memcache执行会到内存中读取libevent-2.0.so.5 库，而该库还未加载到内存中
./memcached: error while loading shared libraries: libevent-2.0.so.5: cannot open shared object file: No such file or directory

[root@bogon bin]# vim /etc/ld.so.conf
[root@bogon bin]# ldconfig   这个命令可以将函数库扔到内存当中，它是按照/etc/ld.so.conf文件中的配置信息来加载内存的，不在此文件中的函数库绝对路径要编辑，此后系统启动后会动态加载，**ldconfig是使得立即生效**

	[root@bogon bin]# vim /etc/ld.so.conf
	[root@bogon bin]# ldconfig 
	[root@bogon bin]#           没有出现错误说明成功


[root@bogon bin]# /usr/local/memcache/bin/memcached 执行
can't run as root without the -u switch    出错，需要-uroot 

[root@bogon bin]# /usr/local/memcache/bin/memcached -uroot -d  添加-uroot，-d是使得它在后台运行

不错的话memcache就能用了

**测试memcache的使用**

	[root@bogon bin]# yum install telnet  先安装telnet

之后，

	[root@bogon bin]# telnet localhost 11211

之后：

	set a 0 0 1   设置一个变量a
	
	set a 0 0 1
	a
	STORED
	get a
	VALUE a 0 1    这一过程就向内存中存了一个字符a
	a
	END
	
	quit  退出
	Connection closed by foreign host.



centos 的RPM包安装，即为编译好的软件包  <br/>
32位平台 要下载i386 i686             <br/>
64位平台 要下载64位x86_64，当然也可以安装32位的，但32位的不能安装64位的

**rpm安装包 卸载删除较容易，数据库记录了安装的信息**

**[root@bogon local]# rpm -qa**   查看安装了多少的rpm包软件

	control-center-extra-2.28.1-40.el6.x86_64
	poppler-0.12.4-10.el6.x86_64
	gnome-python2-gnome-2.28.0-3.el6.x86_64
	dejavu-fonts-common-2.33-1.el6.noarch
	file-roller-2.28.2-7.el6.x86_64
	poppler-utils-0.12.4-10.el6.x86_64
	gnome-utils-libs-2.28.1-10.el6.x86_64



**挂载光盘：管理中设置，光盘处选择光盘载入，将已连接复选框选中**

	[root@bogon local]# mount /dev/cdrom /media/   挂载
	mount: you must specify the filesystem type
	[root@bogon local]# cd /media/   加入media
	[root@bogon media]# ls       可以查看刚才挂载的盘
	CentOS_6.8_Final
	[root@bogon media]# cd CentOS_6.8_Final/
	[root@bogon CentOS_6.8_Final]# ls
	CentOS_BuildTag  isolinux                  RPM-GPG-KEY-CentOS-Debug-6
	EFI              Packages                  RPM-GPG-KEY-CentOS-Security-6
	EULA             RELEASE-NOTES-en-US.html  RPM-GPG-KEY-CentOS-Testing-6
	GPL              repodata                  TRANS.TBL
	images           RPM-GPG-KEY-CentOS-6
	[root@bogon CentOS_6.8_Final]# 

**[root@bogon CentOS_6.8_Final]# find /media/CentOS_6.8_Final -name \*tree\* ** 在/media/CentOS_6.8_Final 目录下按名称 -name   搜索 tree ,*是通配符需要转义
搜索结果

	/media/CentOS_6.8_Final/Packages/tree-1.5.3-3.el6.x86_64.rpm
	/media/CentOS_6.8_Final/.treeinfo

[root@bogon CentOS_6.8_Final]# rpm -ivh /media/CentOS_6.8_Final/Packages/tree-1.5.3-3.el6.x86_64.rpm    rpm安装，i 为安装即install,v 为显示安装进程，h为显示安装进度条

[root@bogon /]# tree  命令生效

**[root@localhost media]# umount CentOS_6.8_Final/   弹出挂载**

----------------------------------------------------------
##rpm查找

**[root@bogon www]# rpm -qa | egrep -i '^tree'   egrep 为以正则的形式查找**，-i为不区分大小写，^为tree为开头

**[root@bogon www]# rpm -qa | egrep -i '^tree'**
tree-1.5.3-3.el6.x86_64   说明软件已经安装

**[root@bogon www]# rpm -e tree-1.5.3-3.el6.x86_64**  这样就删除了，tree就不在生效了，简单
**但**有些带有依赖关系的软件可能不能完全删除成功

**[root@bogon admin]# rpm -qal | egrep -i 'vim' **  显示vim在linux中都安装了哪些文件

**[root@bogon admin]# rpm -qac | egrep -i 'vim'**  查找vim的配置文件

	/etc/libreport/events.d/vimrc_event.conf
	/etc/libreport/events/collect_vimrc_system.xml
	/etc/libreport/events/collect_vimrc_user.xml
	/etc/vimrc

------------------------------------------
##yum 基于网络的来安装

**[root@bogon admin]# vim /etc/yum.repos.d/CentOS-Base.repo**    yum安装时会根据yum源来下载安装文件

**[root@bogon admin]# yum clean all**  清理一下之前安装的内存信息

**[root@bogon admin]# yum install mysql**  安装mysql,它先将文件下载到本地

	[root@bogon admin]# yum install mysql
	Loaded plugins: fastestmirror, refresh-packagekit, security
	Setting up Install Process
	Determining fastest mirrors
	 * base: centos.ustc.edu.cn
	 * extras: centos.ustc.edu.cn
	 * updates: centos.ustc.edu.cn
	base                                                     | 3.7 kB     00:00     
	base/primary_db                                          | 4.7 MB     00:25     
	extras                                                   | 3.4 kB     00:00     
	extras/primary_db                                        |  37 kB     00:00     
	updates                                                  | 3.4 kB     00:00     
	updates/primary_db                                       | 740 kB     00:03     
	Resolving Dependencies
	--> Running transaction check
	---> Package mysql.x86_64 0:5.1.73-7.el6 will be installed
	...
	
	  Installing : mysql-5.1.73-7.el6.x86_64                                    1/1 
	  Verifying  : mysql-5.1.73-7.el6.x86_64                                    1/1 
	
	Installed:
	  mysql.x86_64 0:5.1.73-7.el6                                                   
	
	Complete!
安装完成，测试

	[root@bogon ~]# mysql
	ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)   没显示找不到文件说明已经安装好

**[root@bogon ~]# yum erase mysql**  卸载/删除mysql

**[root@bogon ~]# yum search mysql**  搜索mysql相关

**[root@bogon ~]# yum -y install mysql mysql-server mysql-devel** 安装mysql客户端、服务器端和扩展

	Total download size: 13 M
	Downloading Packages:  自动安装其他依赖包
	(1/12): keyutils-libs-devel-1.4-5.el6.x86_64.rpm         |  29 kB     00:00     
	(2/12): krb5-devel-1.10.3-57.el6.x86_64.rpm              | 504 kB     00:03     
	(3/12): libcom_err-devel-1.41.12-22.el6.x86_64.rpm       |  33 kB     00:00     
	(4/12): libselinux-devel-2.0.94-7.el6.x86_64.rpm         | 137 kB     00:00     
	(5/12): libsepol-devel-2.0.41-4.el6.x86_64.rpm           |  64 kB     00:00     
	(6/12): mysql-devel-5.1.73-7.el6.x86_64.rpm 
	
	...
	Dependency Updated:
	  openssl.x86_64 0:1.0.1e-48.el6_8.1                                            
	
	Complete!

**[root@bogon ~]# service mysqld start**   启动mysql服务器
...
	                                                           	[  OK  ]
	Starting mysqld:                                           [  OK  ]
	[root@bogon ~]# 
	
	You can start the MySQL daemon with:
	cd /usr ; /usr/bin/mysqld_safe &      提示执行此命令可以执行mysql
	
	You can test the MySQL daemon with mysql-test-run.pl
	cd /usr/mysql-test ; perl mysql-test-run.pl
	
	Please report any problems with the /usr/bin/mysqlbug script!
	
	                                                           	[  OK  ]
	Starting mysqld:                                           [  OK  ]
	[root@bogon ~]# 
	[root@bogon ~]# /usr/bin/mysqld_safe &  执行即可
	
	[root@bogon ~]# service mysqld start   启动mysqld
	Starting mysqld:                                           [  OK  ]


[root@bogon ~]# mysql -uroot -p  与dos中一样  <br/>
Enter password: 
----------------------------------------------------
## 安装apache ##
**先yum搜索一下 在centos中叫 httpd**

	[root@bogon ~]# yum search httpd
	
	[root@bogon ~]# yum -y install httpd  安装
	Loaded plugins: fastestmirror, refresh-packagekit, security
	Setting up Install Process
	Loading mirror speeds from cached hostfile
	 * base: centos.ustc.edu.cn
	 * extras: centos.ustc.edu.cn
	 * updates: centos.ustc.edu.cn
	Package httpd-2.2.15-53.el6.centos.x86_64 already installed and latest version
	Nothing to do   这说明已经安装过apache/httpd 
	
	[root@bogon ~]# apachectl start  启动apache
	httpd: apr_sockaddr_info_get() failed for bogon
	httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
	httpd (pid 13836) already running   已经启动
	本地地址栏：http://localhost/可以访问

## 安装php ##
**先搜索yum search php **

	[root@bogon ~]# yum -y install php php-mysql php-gd php-pdo  暂且先安装这几个软件
	...
	Dependency Installed:
	  libXpm.x86_64 0:3.5.10-2.el6             php-cli.x86_64 0:5.3.3-47.el6        
	  php-common.x86_64 0:5.3.3-47.el6        
	
	Complete!

---------------------------------
**PHP是作为apache的扩展来使用的，因此安装完php后要重启apache**

**[root@bogon ~]# apachectl restart**

或者

	[root@localhost chkconfig.d]# service httpd start
	
	[root@bogon ~]# cd /var/www   默认www目录
	[root@bogon www]# ls
	cgi-bin  error  html  icons

**[root@bogon www]# cd html/**  默认访问html放置php的脚本

	[root@bogon html]# touch index.php
	[root@bogon html]# vim index.php  编辑完在浏览器上访问http://localhost/index.php

**在其他计算机浏览器输入这个虚拟机或计算机的ip也可以访问**

**[root@bogon html]# vim /etc/php.in**i  修改配置文件，开启报错error_display=On 

	[root@bogon html]# apachectl restart
	httpd: apr_sockaddr_info_get() failed for bogon
	httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
	[root@bogon html]# vim /etc/httpd/conf/httpd.conf 
	 #ServerName www.example.com:80   修改配置文件，
	 277 ServerName localhost:80   增加这一行

**重启即可**

	[root@bogon html]# apachectl restart  此时不报此问题了
	[root@bogon html]# 
	
	
	[root@localhost Desktop]# apachectl stop  关闭apache

#27  计划和任务

##单一计划任务 at
一直运行的程序叫做服务

只进行单个运行的是进程

**[daiyan9095@bogon Desktop]$ ps aux **  查看所有在运行的服务，相当于win的任务管理器

	USER        PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
	root          1  1.1  0.1  19348  1552 ?        Ss   03:40   0:01 /sbin/init
	root          2  0.0  0.0      0     0 ?        S    03:40   0:00 [kthreadd]


**[daiyan9095@bogon Desktop]$ ps aux | grep atd**   查看单一计划任务服务的进程

	root       2338  0.0  0.0  21108   496 ?        Ss   03:41   0:00 /usr/sbin/atd
	root       2834  0.0  0.0 103320   848 pts/0    S+   03:45   0:00 grep atd

最后一行就是该**查询命令**的进程

程序运行就开启了进程，载入了CPU

一直进行的进程就叫服务

yum install at   安装at软件
	service atd start  启动at，守护进程，该程序启动后就不会自动断开

##关闭开机自动启动atd服务

	[root@localhost www]# chkconfig --level 345 atd off
	[root@localhost www]# chkconfig |grep atd
	atd             0:off   1:off   2:off   3:off   4:off   5:off   6:off


**[root@bogon ~]# date**  查看现在的时间

###设置单一计划
	[root@bogon ~]# date
	Mon Jun 20 03:54:02 PDT 2016
	[root@bogon ~]# at 03:57   设置了单一计划
	at> touch /tmp/www/03.57.txt   该计划生成文件
	at> <EOT>               按ctrl+d退出
	job 1 at 2016-06-20 03:57
	[root@bogon ~]# date
	Mon Jun 20 03:55:08 PDT 2016
	
	[root@bogon ~]# at -l    查看计划信息
	1  2016-06-20 03:57 a root
	
	[root@bogon ~]# at -l  时间已过就没有任何显示了
	[root@bogon ~]# 

**[root@bogon ~]# ls /tmp/www**  创建了该文件
0400.txt 

[root@bogon ~]# at -c 2   查询任务2的详细信息

[root@bogon ~]# at 04:03 2016-06-20   指定具体日期，执行计划
at> rm /tmp/www/0400.txt
at> <EOT>
job 3 at 2016-06-20 04:03

**[root@bogon ~]# at -c 3**    查询任务3的详细信息

	#!/bin/sh
	# atrun uid=0 gid=0
	# mail daiyan9095 0
	umask 22
	...

**[root@bogon ~]# ls /tmp/www/**   计划执行，文件被删除

	admin     backup  image.class.php 

**注意**执行计划者对命令要有权限

**[root@bogon www]# ls >/tmp/www/hd.sh**   不显示结果，仅是将结果输出到文件中

	[root@bogon www]# more hd.sh 

将查询结果输出到文件

	[root@bogon www]# at 04:15 2016-06-20
	at> find / -name \*at\* >/tmp/www/hd.sh   将结果输出到文件
	at> <EOT>
	job 4 at 2016-06-20 04:15
	[root@bogon www]# date
	Mon Jun 20 04:12:17 PDT 2016
	[root@bogon www]# at -l
	4  2016-06-20 04:15 a root
	[root@bogon www]# at -c 4
	#!/bin/sh
	# atrun uid=0 gid=0
	# mail daiyan9095 0

**监听文件内容信息,watch：**

	watch cat top.log


	[root@bogon www]# ls -ld
	drwxr-xr-x. 5 root root 4096 Jun 20 04:11 .

时间到了之后就将内容输出到指定文件了

    1 /boot/efi/EFI/redhat
    2 /boot/grub/fat_stage1_5
    3 /selinux/class/db_language/perms/setattr

## at的配置文件:at.allow  或者 at.deny ##

	[root@bogon www]# cat /etc/at.deny 
                                  是空值，说明所有用户都在拒绝之外，

如果在at.dney中编辑了用户名，那么该用户就没有设定at这个权限

如果某一用户在allow和deny都存在，则以allow为准，即允许
如果有allow文件，不在该文件内的所有用户不能执行at

##周期性计划任务  crontab
该服务为内置，使用前看是否开启，可以

	ps aux |grep cron

开启服务

	[root@localhost etc]# service crond start

**[root@bogon www]# crontab -e**   -e代表的是编辑的意思

	[root@bogon www]# cat /etc/crontab
	SHELL=/bin/bash
	PATH=/sbin:/bin:/usr/sbin:/usr/bin
	MAILTO=root
	HOME=/
	...


# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name command to be executed


**[root@bogon www]# crontab -e** 

      1 * * * * *     这样编辑则代表每一分钟都执行一次

      1 * * * * * echo 1 >/tmp/www/cron.log    即每一分钟将1写入这个文件

**[root@bogon www]# crontab -l**    查看crontab  信息 `* * * * * echo 1 >/tmp/www/cron.log`

	[root@bogon www]# cat cron.log  时间到后已经开始执行了
	1

**[root@bogon www]# crontab -r**   移除该周期计划

**注意[root@bogon www]# echo 1 >hd.sh   这个写入会将原文件内容删除**

**crontab  -l 只显示当前的任务，其他的看不到**

	crontab -e 
	      1 * * * * * date :>/tmp/www/cron.log


[root@bogon www]# watch cat cron.log   watch命令是不断执行某一命令，间隔时间为2秒

	Every 2.0s: cat cron.log                                                   Mon Jun 20 04:44:06 2016

`date >>/tmp/www/cron.log`  **两个>>是向文件中追加内容**，不会覆盖原内容，**而一个>是替换**

这个功能可以每天备份数据

	[root@bogon www]# crontab -r   删除计划
	[root@bogon www]# crontab -l
	no crontab for root
	[root@bogon www]# 

[root@bogon www]# ls /var/spool/cron/   实际存储的计划在这里，编辑的文件就在这里

**[root@bogon www]# ls /var/spool/cron/**
root     以设置计划的用户的名字命名的文件

前边的1是行号，这个计划指 每2 5 8 月的2 3 4 18 日的20-23点的12 23 45 分执行

  1 12,23,45 20-23 2,3,4,18 2,5,8 * date >>/tmp/www/cron.log

这个指的是每个三天的20-23点每三分钟

	1 */3 20-23 */3 2,5,8 * date >>/tmp/www/cron.log


**[root@bogon ~]# service mysqld start**   启动mysql服务器


[root@bogon www]# ps aux | grep cron   查看cron服务

	[root@bogon www]# ps aux | grep cron
	root       2323  0.0  0.1 116876  1440 ?        Ss   03:41   0:03 crond
	root       8876  0.0  0.0 103320   868 pts/0    S+   05:05   0:00 grep cron

	[root@bogon ~]# crontab -l
	32 20 6,10 * * /usr/bin/mysqldump
	 -uroot -p>/tmp/www/test_backup_data   

**命令最好用绝对路径**

在DOS命令行 

	C:\Users\Administrator>mysqldump -uroot -p u>C:\Users\Administrator\Desktop\u.txt

**mysqldump 就是用来将数据库备份的**

#28  进程管理

程序运行时就会变为进程，即程序是通过进程执行操作的

**[root@bogon ~]# ps -l**   查看自己的进程

	F S   UID    PID   PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
	4 S     0   8911   8893  0  80   0 - 41312 wait   pts/1    00:00:00 su
	4 S     0   8917   8911  0  80   0 - 27121 wait   pts/1    00:00:00 bash
	4 R     0   9025   8917  0  80   0 - 27035 -      pts/1    00:00:00 ps

PID和PPID显示父子进程，即父进程进行才能进行子进程



-------------------------------------------
**输出重定向**

ls >/tmp/www/t.txt  替换

ls >>/tmp/www/t.txt   重写

**错误输出重定向,要添加2**

	sfafafafafa 2>/tmp/www/error.logged 

	[root@bogon www]# afafafasfas >error.log
	bash: afafafasfas: command not found
	[root@bogon www]# afafafasfas 2>error.log
	[root@bogon www]# cat error.log 
	bash: afafafasfas: command not found

**[root@bogon www]# fafafafafaf 2>/dev/null**  该文件就相当于一个垃圾桶，输进去的内容消失

	[root@bogon www]# cat /dev/null
	[root@bogon www]# 

###`[liu@bogon www]$ find / -name \*index\*`

	find: `/proc/2401/task/2453/fdinfo': Permission denied  我们会看见有很多的权限限制，这就可以看做错误
	find: `/proc/2401/task/2453/ns': Permission denied
	find: `/proc/2401/task/2454/fd': Permission denied
	find: `/proc/2401/task/2454/fdinfo': Permission denied
	find: `/proc/2401/task/2454/ns': Permission denied
	find: `/proc/2401/task/2455/fd': Permission denied
	find: `/proc/2401/task/2455/fdinfo': Permission denied

**如果我们不希望看到这些错误，那就将错误输出重定向**

`[liu@bogon www]$ find / -name \*index\* 2>/dev/null`   

**将错误扔进垃圾桶，只显示正确的**

	/selinux/class/db_language/index
	/selinux/class/db_sequence/index
	/selinux/class/db_view/index
	/selinux/class/db_schema/index
	/selinux/class/x_keyboard/index
	/selinux/class/x_pointer/index

也可以两个同时用，1代表正确信息

**[liu@bogon www]$ find / -name \*index\* 1>/tmp/ok.txt 2>/dev/null**

[root@bogon www]# userdel -r liu

#31 

[root@bogon www]# yum -y update  更新所有软件等，不用每次y确认
	...
	  libXrender.x86_64 0:0.9.8-2.1.el6_8.1                                        
	  libsmbclient.x86_64 0:3.6.23-35.el6_8                                        
	  libtdb.x86_64 0:1.3.8-3.el6_8.2                                              
	  ntp.x86_64 0:4.2.6p5-10.el6.centos.1                                         
	  ntpdate.x86_64 0:4.2.6p5-10.el6.centos.1                                     
	  openssh.x86_64 0:5.3p1-118.1.el6_8                                           
	  openssh-askpass.x86_64 0:5.3p1-118.1.el6_8                                   
	  openssh-clients.x86_64 0:5.3p1-118.1.el6_8                                   
	  openssh-server.x86_64 0:5.3p1-118.1.el6_8                                    
	  samba-common.x86_64 0:3.6.23-35.el6_8                                        
	  samba-winbind.x86_64 0:3.6.23-35.el6_8                                       
	  samba-winbind-clients.x86_64 0:3.6.23-35.el6_8                               
	  tzdata.noarch 0:2016d-1.el6                                                  
	
	Complete!


**[root@bogon www]# yum -y update 1>/tmp/yum_update.log 2>&1 &**
将更新信息输出到/tmp/yum_update.log中，错误信息也输出到这里&1,最后一个& 指的是让更新操作在后台进行

	[root@bogon www]# jobs即查看后台进程
	
	[root@bogon www]# yum -y update 1>/tmp/www/yum_update.log 2>&1 &
	[1] 20825
	[root@bogon www]# jobs
	[1]+  Done                    yum -y update > /tmp/www/yum_update.log 2>&1
	[root@bogon www]# 
	
	[root@bogon www]# cat yum_update.log 
	Loaded plugins: fastestmirror, refresh-packagekit, security
	Setting up Update Process
	Loading mirror speeds from cached hostfile
	 * base: centos.ustc.edu.cn
	 * extras: mirrors.cug.edu.cn
	 * updates: centos.ustc.edu.cn
	No Packages marked for Update



ctrl+z为将当前运行放到后台这时程序停止运行，**然后再执行命令bg 就可以使得程序在后台运行**

/icons/gnome/24x24/mimetypes/gnome-mime-application-postscript.png
^Z
[1]+  Stopped                 find / -name \*cat\*

**如果按fg则将后台返回前台继续运行**
	
	[root@bogon www]# ps -l   查看当前用户的进程
	
	[root@bogon www]# vim index.php 
	[1]+  Stopped                 vim index.php
	[root@bogon www]# jobs
	[1]+  Stopped                 vim index.php
	[root@bogon www]# 

[root@bogon www]# ps -l  看到了vim进程

	F S   UID    PID   PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
	4 S     0   9182   9166  0  80   0 - 41312 wait   pts/0    00:00:00 su
	4 S     0   9190   9182  0  80   0 - 27121 wait   pts/0    00:00:00 bash
	4 S     0   9325   9190  0  80   0 - 41279 wait   pts/0    00:00:00 su
	4 R     0   9328   9325  0  80   0 - 27121 -      pts/0    00:00:00 bash
	0 T     0  20866   9328  0  80   0 - 35022 signal pts/0    00:00:00 vim
	4 R     0  20867   9328  0  80   0 - 27035 -      pts/0    00:00:00 ps

**结束进程**

	[root@bogon ~]# ps -l
	F S   UID    PID   PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
	4 S     0   2794   2779  0  80   0 - 41312 wait   pts/0    00:00:00 su
	4 S     0   2802   2794  0  80   0 - 27121 wait   pts/0    00:00:00 bash
	4 R     0   2838   2802  0  80   0 - 27036 -      pts/0    00:00:00 ps

**[root@bogon ~]# kill 2794    正常关闭程序**

	[root@bogon ~]# 
	Session terminated, killing shell... ...killed.
	Terminated
	[daiyan9095@bogon ~]$ ps -l
	F S   UID    PID   PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
	0 S   500   2779   2777  0  80   0 - 27088 wait   pts/0    00:00:00 bash
	0 R   500   2846   2779  2  80   0 - 27036 -      pts/0    00:00:00 ps


	[root@bogon www]# vim cron.log 
	[1]+  Stopped                 vim cron.log
	[root@bogon www]# jobs
	[1]+  Stopped                 vim cron.log
	[root@bogon www]# ps -l
	F S   UID    PID   PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
	4 S     0   2898   2779  0  80   0 - 41312 wait   pts/0    00:00:00 su
	4 S     0   2906   2898  0  80   0 - 27121 wait   pts/0    00:00:00 bash
	0 T     0   2917   2906  0  80   0 - 34751 signal pts/0    00:00:00 vim
	4 R     0   2919   2906  0  80   0 - 27036 -      pts/0    00:00:00 ps
	[root@bogon www]# kill 2971
	bash: kill: (2971) - No such process

**[root@bogon www]# kill 2917   正常关闭，如果关闭不成功也不会再次关闭**

	[root@bogon www]# ps -l
	F S   UID    PID   PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
	4 S     0   2898   2779  0  80   0 - 41312 wait   pts/0    00:00:00 su
	4 S     0   2906   2898  0  80   0 - 27121 wait   pts/0    00:00:00 bash
	0 T     0   2917   2906  0  80   0 - 34751 signal pts/0    00:00:00 vim
	4 R     0   2920   2906  0  80   0 - 27035 -      pts/0    00:00:00 ps

**由此可见vim进程并没有关闭成功**

**[root@bogon www]# kill -9 2917   该命令是强制关闭进程**

	[root@bogon www]# ps -l
	F S   UID    PID   PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
	4 S     0   2898   2779  0  80   0 - 41312 wait   pts/0    00:00:00 su
	4 S     0   2906   2898  0  80   0 - 27121 wait   pts/0    00:00:00 bash
	4 R     0   2922   2906  0  80   0 - 27034 -      pts/0    00:00:00 ps
	[1]+  Killed                  vim cron.log


	[root@bogon www]# jobs
	[1]+  Stopped                 find / -name \*a\*
	[root@bogon www]# ps -l
	F S   UID    PID   PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
	4 S     0   2898   2779  0  80   0 - 41312 wait   pts/0    00:00:00 su
	4 S     0   2906   2898  0  80   0 - 27121 wait   pts/0    00:00:00 bash
	0 T     0   2955   2906  0  80   0 - 28071 signal pts/0    00:00:00 find
	4 R     0   2957   2906  4  80   0 - 27036 -      pts/0    00:00:00 ps

**存在find进程，状态为T代表暂停**

##关闭进程

**kill 进程ID**
   
**kill -9 进程ID  强制关闭** 

**pkill 进程名   该命令是以进程名(CMD)来关闭**

**pkill  -9 进程名  该命令是以进程名(CMD)来强制关闭**

**killall -9 -i  进程名  该命令也是按照进程名称来关闭进程   i是确认的意思**
	
	[root@bogon www]# pkill -9 find
	[1]+  Killed                  find / -name \*a\*
	
	
	[root@bogon www]# killall -9 -i vim
	Signal vim(2964) ? (y/N) y
	[1]+  Killed                  vim hd.sh


**jobs 查看后台运行的程序**


**ps  相当于任务管理**

**ps  aux 显示所有的进程**

**ps aux | more  分屏显示该命令的结果**

	[root@bogon www]# ps aux | more
	USER        PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
	root          1  0.1  0.1  19348  1548 ?        Ss   16:45   0:02 /sbin/init
	root          2  0.0  0.0      0     0 ?        S    16:45   0:00 [kthreadd]
	root          3  0.0  0.0      0     0 ?        S    16:45   0:00 [migration/0]

root 代表由那个用户启动的命令

PID  为系统为每一个进程分配的ID

CPU  使用率

MEM  内存使用率

VSZ 虚拟内存

RSS  显示的内存大小

TTY  为目前该进程所在的终端号，并不是每个进程的执行都要有终端，no login 所以有?

STAT  显示进程的状态

       S  代表休眠，有小s代表有子进程

START  代表进程启动时间

TIME  代表该进程使得CPU运算了多长时间

COMMAND   代表进程由那个命令产生的

我们主要关注CPU使用率、PID和COMMAND


**[root@bogon www]# ps aux | grep httpd  查看是否开启了apache**

	root       3008  0.0  0.0 103316   860 pts/0    S+   17:22   0:00 grep httpd
	[root@bogon www]# apachectl start  开启apache
	[root@bogon www]# ps aux | grep httpd
	root       3012  4.6  0.9 279928  9628 ?        Ss   17:22   0:00 /usr/sbin/httpd -k start
	apache     3014  0.0  0.5 279928  5436 ?        S    17:22   0:00 /usr/sbin/httpd -k start
	apache     3015  0.0  0.5 279928  5420 ?        S    17:22   0:00 /usr/sbin/httpd -k start
	apache     3016  0.0  0.5 279928  5420 ?        S    17:22   0:00 /usr/sbin/httpd -k start
	apache     3017  0.0  0.5 279928  5420 ?        S    17:22   0:00 /usr/sbin/httpd -k start
	apache     3018  0.0  0.5 279928  5420 ?        S    17:22   0:00 /usr/sbin/httpd -k start
	apache     3019  0.0  0.5 279928  5420 ?        S    17:22   0:00 /usr/sbin/httpd -k start
	apache     3020  0.0  0.5 279928  5420 ?        S    17:22   0:00 /usr/sbin/httpd -k start
	apache     3021  0.0  0.5 279928  5420 ?        S    17:22   0:00 /usr/sbin/httpd -k start
	root       3023  0.0  0.0 103316   864 pts/0    S+   17:22   0:00 grep httpd



**[root@bogon www]# service mysqld start  启动mysql**

	Starting mysqld:                                           [  OK  ]
	[root@bogon www]# ps aux | grep mysql
	root       3081  0.1  0.1 108216  1528 pts/0    S    17:26   0:00 /bin/sh /usr/bin/mysqld_safe --datadir=/var/lib/mysql --socket=/var/lib/mysql/mysql.sock --pid-file=/var/run/mysqld/mysqld.pid --basedir=/usr --user=mysql
	mysql      3183  7.2  1.7 377528 17752 pts/0    Sl   17:26   0:01 /usr/libexec/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --log-error=/var/log/mysqld.log --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/lib/mysql/mysql.sock
	root       3208  0.0  0.0 103316   864 pts/0    S+   17:26   0:00 grep mysql


**[root@bogon www]# which mysql **

	/usr/bin/mysql

**[root@bogon www]# /usr/bin/mysqld_safe &   这个也是启动mysql**

	[1] 3226
	[root@bogon www]# 160620 17:28:37 mysqld_safe Logging to '/var/log/mysqld.log'.
	160620 17:28:37 mysqld_safe A mysqld process already exists

#31 

**要复制的文件夹下存在目录等，要递归拷贝**

	[root@localhost backup]# cp -r ~daiyan9095 .


	[root@bogon www]# pstree 以树状格式显示进程  
	init─┬─ManagementAgent───2*[{ManagementAgen}]
	     ├─NetworkManager─┬─dhclient
	     │                └─{NetworkManager}


	[root@bogon www]# pstree -p  以树状格式显示进程,并且显示进程ID
	[root@bogon www]# pstree -p
	init(1)─┬─ManagementAgent(1569)─┬─{ManagementAgen}(1578)
	        │                       └─{ManagementAgen}(1580)
	        ├─NetworkManager(1966)─┬─dhclient(1994)
	        │                      └─{NetworkManager}(1995)


	root@bogon www]# pstree -u  附带显示进程由那个用户开启
	init─┬─ManagementAgent───2*[{ManagementAgen}]
	     ├─NetworkManager─┬─dhclient
	     │                └─{NetworkManage


**[root@bogon www]# w  查看 CPU运行的负载**

	 17:34:31 up 49 min,  2 users,  load average: 0.69, 0.32, 0.27
	USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
	daiyan90 tty1     :0               16:46   48:50  36.50s  0.30s pam: gdm-password
	daiyan90 pts/0    :0.0             16:47    0.00s  1.57s 14.94s /usr/bin/gnome-terminal -x /

**[root@bogon www]# uptime  当前时间和当前用户及当前的负载**

	 17:35:30 up 50 min,  2 users,  load average: 0.60, 0.40, 0.31

**[root@bogon www]# top  该命令更详细的显示信息，而且每2秒刷新显示结果**
	
	top - 17:36:59 up 51 min,  2 users,  load average: 0.54, 0.41, 0.32
	Tasks: 158 total,   1 running, 157 sleeping,   0 stopped,   0 zombie
	Cpu(s):  6.8%us,  1.7%sy,  0.0%ni, 91.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
	Mem:   1004136k total,   592172k used,   411964k free,    26752k buffers
	Swap:  2031612k total,        0k used,  2031612k free,   229888k cached

17:36:59 为现在linux的时间

Tasks: 158 total  共有158个进程在跑

1 running 1个进程正在跑 

157 sleeping 157个进程在休眠

0 stopped 没有停止的进程

0 zombie  僵尸进程，即父进程结束而子进程未结束，**要删掉已经无法调用否则占用CPU**

Cpu(s):  6.8%us,  1.7%sy 指用户和系统使用的CPU

	Mem:   1004136k total,   592172k used,   411964k free,    26752k buffers
	内存   一共的内存          被使用的            还剩余          变为缓冲区的内存
	Swap:  2031612k total,        0k used,         2031612k free,   229888k cached
	交换分区              被使用的（为0较好，否则考虑增加内存）    还剩余             

**load average: 0.54, 0.41, 0.32   代表负载
0.32  小于0.7还可以 **

**按q退出** 

在top状态，按下M 则按照内存使用多少进行排序，P 按CPU使用率排序，N 按pid排序

**top -d 10   则每10秒刷新一次**

	[root@bogon www]# crontab -l
	*/1 * * * * /usr/bin/top -b >>/tmp/www/top.log   

**要加-b才能统计到该信息，因为这里有交互界面**

	[root@bogon www]# ps aux |grep cron
	root       2331  0.0  0.1 116900  1544 ?        Ss   16:46   0:03 crond
	root       3574  0.0  0.0 103320   868 pts/0    S+   18:18   0:00 grep cron
	[root@bogon www]# watch cat top.log 
	
	*/1 * * * * /usr/bin/top -b >>/tmp/www/top.log

每隔1分钟     **要用绝对路径**

#33 

进程与服务

软件-》运行-》普通进程

软件-》一直运行-》服务

mysqld apache httpd sshd  =>服务

#34 

###系统启动流程:
	1\开启电源
	2、bios检测硬件
	3、启动设备硬盘（硬盘最开始位置）读取小程序MBR boot loader
	4\加载内核kernel 
	5\执行进程 init ，其PID=1
	6、执行/etc/rc.sysinit ，做些初始化工作
	7、/etc/inittab  根据文件内容启用相应的工作,找到相依你给的级别的目录
	8、/etc/rc.d/rc5.d     级别Wie5，则到该目录下启动第一个字母为s的
	9、运行/etc/rc.local 
	10/出现用户登录界面

更改/etc/inittab  
 25 # 
 26 id:3:initdefault:

reboot后只有命令行界面
在命令行界面再次更改后reboot即可

#35

切换启动级别

**在root账户，输入命令init 3 直接到3号级别，即为命令行界面**

**该命令执行流程：**

先到rc5.d里看那些与3的一致不变动，执行与3不同的，所以较快因为有些不用再次启动了

`[root@bogon www]# chkconfig  --list`  **查询服务的设置**

	NetworkManager    0:off 1:off 2:on  3:on  4:on  5:on  6:off
	abrt-ccpp         0:off 1:off 2:off 3:on  4:off 5:on  6:off
	abrtd             0:off 1:off 2:off 3:on  4:off 5:on  6:off
	acpid             0:off 1:off 2:on  3:on  4:on  5:on  6:off


`[root@bogon www]# chkconfig --list |more`   **是分屏显示**


`[root@bogon www]# chkconfig | grep mysql`  **查看指定的服务**

	mysqld            0:off 1:off 2:off 3:off 4:off 5:off 6:off


**[root@bogon www]# chkconfig --level 345 mysqld on  设置mysql在345级别时自动开启服务**

**grep  是对结果集查找**


	[root@bogon www]# ll /etc/rc3.d  
	lrwxrwxrwx. 1 root root 10 Jun 13 15:18 /etc/rc3.d -> rc.d/rc3.d

**其实这都是软链接，前面是l**

**chkconfig --help 查看帮助信息**

**[root@bogon www]# ntsysv  这个命令可以通过图形界面开启某些服务，不建议使用**

	[root@bogon www]# service mysqld start
	Starting mysqld:                                           [  OK  ]
	[root@bogon www]# service mysqld status
	mysqld (pid  4434) is running...
	[root@bogon www]# service mysqld stop
	Stopping mysqld:                                           [  OK  ]

#36 公网私有IP地址DNS服务域名主机等详解

	 IP  -----                          DNS服务器
	42.121.125.171:80(w3cschool的IP)     将www.w3c.com和ip对应上 

**IPV4 的IP地址为  32位**  

0000000000000000000000000000000  0与1的组合

转换为10进制则为4个8位，每个位 0-255

**255 255 255 255      最后的80为端口，不同的端口提供不同的服务**

**域名解析--将IP和地址 匹配关系放在DNS中**
 
**端口：**

    httpd 80 
    mysqld 3306
    vsftp 20 21 
    memcache 11211

**bbs.w3c.com/index.php   实际访问的就可能是42.121.125.171:80**

而80代表httpd,即apache,从而服务器就会让apache软件来服务，开启apache后这个软件就开始监听该端口

可能到/var/www/html/bbs下找index.php文件 ，执行动作在将结果返回给客户端

[root@bogon ~]# ifconfig   相当于win下的ipconfig

	让本地win下的浏览器访问虚拟主机linux服务器
	1、在linux下打开apache
	2\在linux的www目录建立相应的文件index.php 
	3\设置命令：iptables -F 
	            setenforce 0
	3\在win的浏览器中输入linux服务器ip即可访问
	
	端口就是要请求的服务

**setenforce是Linux的selinux防火墙配置命令** 执行setenforce 0 表示关闭selinux防火墙

**getenforce是获得该配置的设置**

	[root@localhost Desktop]# getenforce
	Disabled


#37 

**ip 端口 域名 DNS(匹配域名和IP)    浏览器默认端口为80**

	[root@bogon ~]# ifconfig
	eth0      Link encap:Ethernet  HWaddr 00:0C:29:1C:6A:FF  
	          inet addr:192.168.15.129  Bcast:192.168.15.255  Mask:255.255.255.0
	          inet6 addr: fe80::20c:29ff:fe1c:6aff/64 Scope:Link
	          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
	          RX packets:3428 errors:0 dropped:0 overruns:0 frame:0
	          TX packets:299 errors:0 dropped:0 overruns:0 carrier:0
	          collisions:0 txqueuelen:1000 
	          RX bytes:280623 (274.0 KiB)  TX bytes:29817 (29.1 KiB)
	
	lo        Link encap:Local Loopback  
	          inet addr:127.0.0.1  Mask:255.0.0.0
	          inet6 addr: ::1/128 Scope:Host
	          UP LOOPBACK RUNNING  MTU:65536  Metric:1
	          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
	          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
	          collisions:0 txqueuelen:0 
	          RX bytes:1440 (1.4 KiB)  TX bytes:1440 (1.4 KiB)

etho本地网卡
lo本地网址

**配置网卡**

`vim /etc/sysconfig/network-scripts/ifcfg-eth0`

	  1 DEVICE="eth0"     设备名称，不动
	  2 BOOTPROTO="dhcp"   所使用的协议，默认是dhcp,即通过路由动态获得ip,如果是static则为静态ip
	  3 HWADDR="00:0C:29:1C:6A:FF"   网卡的mac地址，不动
	  4 IPV6INIT="yes"
	  5 NM_CONTROLLED="yes"   设置是否使用图形化的软件进行管理
	  6 ONBOOT="yes"     设置开机是否自动激活
	  7 TYPE="Ethernet"    类型：以太网卡，不动
	  8 UUID="80b5601c-1c81-41b5-bec8-218b545c2268"  设备识别出来的一个唯一的UUID，不动
	 9 #the following things are added by me-daiyan9095 下面的内容是我自己加的
	 10 IPADDR=192.168.1.25   一个没有本占用的IP
	 11 NETMASK=255.255.255.0  子网掩码
	 12 GATEWAY=192.168.1.1    网关，数据包要通过这个发出
	 13 DNS1=8.8.8.8      DNS解析器，可以有多个

**[root@localhost ~]# system-config-network**  这个是图形化的更改网络设置，不推荐使用

**[root@localhost ~]# chkconfig NetworkManager off**  关闭图形化界面,不要关闭否则可能连不上网

	[root@bogon ~]# chkconfig --list | grep net
	netconsole        0:off 1:off 2:off 3:off 4:off 5:off 6:off
	netfs             0:off 1:off 2:off 3:on  4:on  5:on  6:off
	network           0:off 1:off 2:on  3:on  4:on  5:on  6:off

**[root@bogon ~]# service network restart**

	Shutting down interface eth0:  Device state: 3 (disconnected)
                                                                 	[  OK  ]
	Shutting down loopback interface:                          [  OK  ]
	Bringing up loopback interface:                            [  OK  ]
	Bringing up interface eth0:  Active connection state: activating
	Active connection path: /org/freedesktop/NetworkManager/ActiveConnection/1
	state: activated
	Connection activated
                                                           	[  OK  ]


##**[root@localhost ~]# /etc/init.d**   这里列出了所有可启动的服务

想启动那个服务就打命令   **service 列表中的命令名  start**

**或者 /etc/init.d/服务名 start**   这个兼容性更好，上面的命令在某系linux系统中不存在

ping 看一看网络是否通,相互检测

	[root@bogon ~]# ping -c 2 baidu.com
	PING baidu.com (111.13.101.208) 56(84) bytes of data.
	64 bytes from 111.13.101.208: icmp_seq=1 ttl=128 time=23.7 ms
	64 bytes from 111.13.101.208: icmp_seq=2 ttl=128 time=13.5 ms

64 发送数据包的大小
2表示ping的次数

host  www.baidu.com   查看baidu的主机IP

	[root@bogon ~]# host www.baidu.com
	www.baidu.com is an alias for www.a.shifen.com.
	www.a.shifen.com has address 220.181.111.188
	www.a.shifen.com has address 220.181.112.244

**[root@bogon ~]# nslookup www.baidu.com **  查看IP信息等

	Server:     192.168.15.2
	Address: 192.168.15.2#53
	Non-authoritative answer:
	www.baidu.com  canonical name = www.a.shifen.com.
	Name: www.a.shifen.com
	Address: 220.181.112.244
	Name: www.a.shifen.com
	Address: 220.181.111.188

**[root@localhost ~]# netstat -a**  查看所有监听的端口，-a表示所有

**[root@localhost ~]# netstat -a |more  分屏查看**

**[root@localhost ~]# netstat -at**   查看基于tcp的端口，-p表示tcp
	Active Internet connections (servers and established)
	Proto Recv-Q Send-Q Local Address               Foreign Address             State      
	tcp        0      0 *:mysql                     *:*                         LISTEN      
	tcp        0      0 *:ssh                       *:*                         LISTEN      
	tcp        0      0 localhost:ipp               *:*                         LISTEN      
	tcp        0      0 localhost:smtp              *:*                         LISTEN      
	tcp        0      0 *:ssh                       *:*                         LISTEN      
	tcp        0      0 localhost:ipp               *:*                         LISTEN      
	tcp        0      0 localhost:smtp              *:*                         LISTEN 

	[root@bogon ~]# netstat -a | grep mysql  查看mysql端口
	tcp        0      0 *:mysql                     *:*                         LISTEN      
	unix  2      [ ACC ]     STREAM     LISTENING     13364  /var/lib/mysql/mysql.sock

**[root@localhost ~]# netstat -l |more    -l表示显示所有监听的端口**

**[root@localhost ~]# netstat -tl |more  显示tcp的**

	[root@localhost ~]# netstat -tlp |more  p表示显示pid
	Active Internet connections (only servers)
	Proto Recv-Q Send-Q Local Address               Foreign Address             State       PID/P
	rogram name   
	tcp        0      0 *:mysql                     *:*                         LISTEN      2265/
	mysqld         
	tcp        0      0 *:ssh                       *:*                         LISTEN      2081/

##ssh链接  ---本地

	[root@bogon ~]# ssh d_1@192.168.15.129
	reverse mapping checking getaddrinfo for bogon [192.168.15.129] failed - POSSIBLE BREAK-IN ATTEMPT!
	d_1@192.168.15.129's password: 
	[d_1@bogon ~]$ 


**不希望账号登录，只能使用，就设置nologin，即不能获得shell**

	[root@bogon ~]# useradd -s /sbin/nologin yahoo
	
	[root@bogon ~]# useradd -s /sbin/nologin tom
	[root@bogon ~]# su tom
	This account is currently not available.
	[root@bogon ~]# passwd tom
	Changing password for user tom.
	New password: 
	BAD PASSWORD: it is based on a dictionary word
	Retype new password: 
	passwd: all authentication tokens updated successfully.
	[root@bogon ~]# su tom
	This account is currently not available.
	[root@bogon ~]# su tom
	This account is currently not available.
	[root@bogon ~]# ssh tom@192.168.15.129
	reverse mapping checking getaddrinfo for bogon [192.168.15.129] failed - POSSIBLE BREAK-IN ATTEMPT!
	tom@192.168.15.129's password: 
	This account is currently not available.
	Connection to 192.168.15.129 closed.   nologin就关闭

#远程登录

**ssh  和vnc**

ssh 是加密传输的

	[root@bogon ~]# /etc/init.d/sshd stop
	Stopping sshd:                                             [  OK  ]
	[root@bogon ~]# /etc/init.d/sshd start
	Starting sshd:                                             [  OK  ]

[root@bogon ~]# ssh root@192.168.15.129 cat /etc/passwd  在ssh之后直接执行命令

**scp可以实现上传和下载**

	[root@bogon www]# scp daiyan9095@192.168.15.129:/tmp/www/index.php /tmp/www/a.index


##VNC
1、安装vnc服务器端

**VNC  远程连接的软件图形化界面**

	[root@bogon ~]# yum search vnc
	[root@bogon ~]# yum -y install tigervnc-server.x86_64  安装软件，这是服务器端

2、在另一个系统中安装vnc客户端

在客户端win下或mac下安装realvnc

3、修改配置文件

	[root@bogon ~]# vim /etc/sysconfig/vncservers 
	19 # VNCSERVERARGS[2]="-geometry 800x600 -nolisten tcp -localhost
	20 # VNCSERVERS="2:sohu 3:qq 4:yahoo"

4、 设置svc密码
[sohu@bogon ~]# vncpasswd sohu   这时要切换到sohu的shell

**只有这些密码都设置完成才能启动vnc服务，否则报错**

5、启动服务--一定要切换到root才能开启

	[root@bogon ~]# service vncserver start
	Starting VNC server: 2:sohu xauth:  file /home/sohu/.Xauthority does not exist
	xauth: (stdin):1:  bad display name "bogon:2" in "add" command
	
	New 'bogon:2 (sohu)' desktop is bogon:2
	
	Creating default startup script /home/sohu/.vnc/xstartup
	Starting applications specified in /home/sohu/.vnc/xstartup
	Log file is /home/sohu/.vnc/bogon:2.log
	
	3:qq 
	You will require a password to access your desktops.
	
	getpassword error: Inappropriate ioctl for device
	Password:4:yahoo runuser: user yahoo does not exist


[root@bogon ~]# netstat -tlp 查看已经开启

	Active Internet connections (only servers)
	Proto Recv-Q Send-Q Local Address               Foreign Address             State       PID/Program name   
	tcp        0      0 *:mysql                     *:*                         LISTEN      2306/mysqld         
	tcp        0      0 *:5902                      *:*                         LISTEN      3766/Xvnc     

6、连接
在win下打开realvnc,直接输入192.168.15.129:2  前边是linux的动态ip,2是配置文件中的账户

然后输入密码，即登录了远程桌面


总结：2种登录 ssh(推荐)   svn
















#38 






                                         


#41 samba共享

**[root@bogon ~]# yum search samba**
他是一个软件，作为服务来运行

**[root@bogon ~]# yum -y install samba**

**作为服务一般放在了/etc/init.d中**

	[root@bogon init.d]# service smb start  开启服务
	Starting SMB services:                                     [  OK  ]
	[root@bogon init.d]# ps aux |grep smb  查看进程是否哦启动
	root       3161  0.0  0.3 213568  3780 ?        Ss   00:41   0:00 smbd -D
	root       3163  0.0  0.1 214092  1996 ?        S    00:41   0:00 smbd -D
	root       3168  1.0  0.0 103316   864 pts/0    S+   00:41   0:00 grep smb

**如果想每次开机自动运行，要设置：**

	chkconfig --level 35 smb on
	chkconfig --list 35 |grep smb

iptables -F 为关掉防火墙

练习smb时先关掉防火墙，更改一下文件

[root@bogon init.d]# iptables -F

[root@bogon init.d]# vim /etc/selinux/config  将sel 向改为disabled,之前为enforcing

	[root@bogon init.d]# iptables -F
	[root@bogon init.d]# vim /etc/selinux/config
	[root@bogon tmp]# setenforce 0
	[root@bogon init.d]# service iptables save
	iptables: Saving firewall rules to /etc/sysconfig/iptables:[  OK  ]

**[root@bogon init.d]# ps aux |grep s |more  这个|就是一个多重选项符**

[root@bogon init.d]# netstat -tnulap |grep smb  查看以下状态 
以上操作服务已经运行

配置： 


1、更改

    101   security = share          
    # daiyan9095  zhiqianshi user  注释行不要加命令行的后边，会出错
    102   passdb backend = tdbsam

2、添加共享目录

    246 #============================ Share Definitions ==============================
    247 [houdunwang]
    248   path=/tmp/www    共享目录
    249   public=yes       所有用户都看得见


	247 #============================ Share Definitions ==============================
	248 [www]
	249   path=/tmp/www
	250   public=yes
	251 [hd]
	252   path=/tmp/hd
	253   public=yes

**在win文件夹地址栏输入 \\linux的ip**
\\192.168.15.129 



#42 

**[root@bogon tmp]# testparm /etc/samba/smb.conf   linux自带的检查命令**

	Load smb config files from /etc/samba/smb.conf
	rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
	Processing section "[www]"
	Processing section "[hd]"
	Processing section "[homes]"
	Processing section "[printers]"
	WARNING: The security=share option is deprecated
	Loaded services file OK.
	Server role: ROLE_STANDALONE
	Press enter to see a dump of your service definitions

**samba设置密码**

	 93 # ----------------------- Standalone Server Options ------------------------
	 94 #
	 95 # Scurity can be set to user, share(deprecated) or server(deprecated)
	 96 #
	 97 # Backend to store user information in. New installations should 
	 98 # use either tdbsam or ldapsam. smbpasswd is available for backwards 
	 99 # compatibility. tdbsam requires no further configuration.
	100 
	101   security = user   这样就需要密码才能登陆
	102   passdb backend = tdbsam

重启
[root@bogon tmp]# vim /etc/samba/smb.conf 
[root@bogon tmp]# service smb restart
Shutting down SMB services:                                [  OK  ]
Starting SMB services:                                     [  OK  ]
之前没有修改过防火墙的要修改，修改selinux，等参照上面
samba需要用他自己的方法设置密码
[root@bogon tmp]# smbpasswd -a daiyan9095
New SMB password:
Retype new SMB password:
Added user daiyan9095.


要想可写：
263   browseable = no
264   guest ok = no
265   writable = yes  这一项，参照注释
266   create mode = 0666 这一项可以控制创建的文件的权限
267  directory mode = 0666 这一项可以控制创建的目录的权限
268  valid users lisi,wang,@p 这一项可以控制只能lisi和wang和组p访问




usermod -G code liu  设置附加组

usermod -G '' liu  删除附加组

#43 

任务：
创建组 design
共享目录/etc/www/design 
组中成员只能更改自己的文件
同组中的其他用户可以查看同组成员文件
除了本组以外的用户不可以查看design找个文件

[root@bogon www]# chmod 1770 design   design文件权限
drwxrwxrwt. 2 root       root           4096 Jun 21 02:49 design
t 表示同组所有创建文件的用户只能修改自己的不能删除别人的



usermod -s /sbin/nologin w2  w2不会获得shell,从而也就不能登陆

###删除之前win缓存的之前链接的账号

	C:\Users\Administrator>net use * /del
	你有以下的远程连接:
	
	                    \\192.168.15.129\IPC$
	继续运行会取消连接。
	
	你想继续此操作吗? (Y/N) [N]: y
	命令成功完成。


#45 

[root@bogon samba]# yum -y update &  后台运行

1、保证软件是最新的

2、root密码要复杂，并长期更换

3、sudo 的用户要绝对信任

4、不要对用户给文件或目录设置过高的权限 文件644 目录 755

5、文件权限不要加x,即执行

6、不要随便使得用户登录服务器 SSH  VNC  SAMBA

**批量更改文件权限**

软件操作文件时也是以一个用户身份进行的，如果文件权限设置过高，就可能导致软件不能操作文件
如apache，它是以第三人来执行文件的，即others,所以在相应文件上设置所有者和组为apache

[root@bogon html]# find /var/www/ -type d  查找指定文件夹下的目录，不包括文件

	/var/www/
	/var/www/html
	/var/www/cgi-bin
	/var/www/error
	/var/www/error/include
	/var/www/icons
	/var/www/icons/small

**[root@bogon html]# find /var/www/ -type d -exec chmod 0755 {} \;**
这就是查找和计划，将目录都改为0755

[root@bogon html]# chmod -R 0644 /var/www/;
这就是查找和计划，将文件和目录都改为0644，然后再执行上一步，将目录更改权限

**[root@bogon html]# find /var/www/ ！-type d -exec chmod 0755 {} \;**
这就是查找和计划，将不是目录的都改为0755

**[root@bogon html]# find /var/www/ -not -type d -exec chmod 0755 {} \;**
这就是查找和计划，将不是目录的都改为0755

**[root@bogon html]# find /var/www/html -type d -exec chmod 0755 {} \;**
**[root@bogon html]# find /var/www/html ! -type d -exec chmod 0644 {} \;**


#46 iptables 防火墙定义思路与实例

www目录的所有者要换为apache

iptables  linux的防火墙

1、防火墙是内核包含的，运行速度很快
2、防火墙从上向下匹配，只要匹配到规则就不再向下匹配

	[root@bogon etc]# iptables -L  显示防火墙的详细信息
	Chain INPUT (policy ACCEPT)      数据包进入规则
	target     prot opt source               destination         
	
	Chain FORWARD (policy ACCEPT)    数据包转发规则
	target     prot opt source               destination         
	
	Chain OUTPUT (policy ACCEPT)     数据包出去的规则
	target     prot opt source               destination   

规则：
  1、访问web服务(apache)允许；
  2、访问mysql不允许
  3、访问memcache不允许

[root@bogon etc]# rpm -qa |grep iptables 查找某个rmp包是否安装
iptables-1.4.7-16.el6.x86_64    有提示说明已经安装
iptables-ipv6-1.4.7-16.el6.x86_64

[root@bogon var]# rpm -qa iptables
iptables-1.4.7-16.el6.x86_64

**数据包的处理方式：**

     1、ACCEPT 接受数据包进来
     2、DROP  直接丢弃数据包
     3、REJECT 丢弃数据包并告知客户端

防火墙规则编写：

[root@bogon etc]# iptables -A INPUT -j DROP   所有进来的数据包直接丢掉，客户端总是在等待响应

**[root@bogon etc]# iptables -L  查看规则**

	Chain INPUT (policy ACCEPT)
	target     prot opt source               destination         
	DROP       all  --  anywhere             anywhere    这就是刚才建立的

	[root@bogon etc]# ls -ld /var/www
	drwxr-xr-x. 6 apache apache 4096 Jun 13 15:19 /var/www
	[root@bogon etc]# ls -ld /var/www/html
	drwxr-xr-x. 3 root root 4096 Jun 21 17:17 /var/www/html

**[root@bogon etc]# iptables -F   清掉所有防火墙规则**

	[root@bogon etc]# iptables -L  清掉后在查看就为空了
	Chain INPUT (policy ACCEPT)
	target     prot opt source               destination         
	
	Chain FORWARD (policy ACCEPT)
	target     prot opt source               destination         
	
	Chain OUTPUT (policy ACCEPT)
	target     prot opt source               destination 

**规则参数：**

	-A  追加
	-I  插入
	-P  默认规则 
	-F 清除规则
	-s 来源
	-D 删除规则 
	--line-number  显示规则序号
	-L 显示规则列表
	--dport  目标端口，与协议p一起使用
	--sport  源端口   对于出数据包 这就成为目标端口了
	-p  指定协议
	-i   指定数据包进入的网卡
	-o   指定数据包出去的网卡

	[root@bogon ~]# iptables -A OUTPUT -p tcp --sport 1035 -j DROP


就是policy后面的单词,只有没有规则时才看默认的规则设置或者所有的规则都不匹配(不明确说接受或拒绝)

**[root@bogon etc]# iptables -L -n --line-number**  显示规则编号，这时可以将规则插入到指定位置

**[root@bogon etc]# iptables -A INPUT -s 192.168.1.1 -j DROP**
-s  指定数据包来源

**[root@bogon etc]# iptables -P INPUT DROP   该默认规则为DROP**

**[root@bogon etc]# iptables -D INPUT 1   删除INPUT里的第一条规则**

#47 

	[root@bogon etc]# iptables -A INPUT -s 192.168.1.1 -j ACCEPT
	[root@bogon etc]# iptables -P INPUT DROP  设置默认项时才能直接加动作，否则要-j
	[root@bogon etc]# iptables -A INPUT DROP
	Bad argument `DROP'
	Try `iptables -h' or 'iptables --help' for more information.
	[root@bogon etc]# iptables -A INPUT -j DROP
	[root@bogon etc]# iptables -L -n --line-number
	Chain INPUT (policy DROP)
	num  target     prot opt source               destination         
	1    ACCEPT     all  --  192.168.1.1          0.0.0.0/0           
	2    DROP       all  --  0.0.0.0/0            0.0.0.0/0           

	Chain FORWARD (policy ACCEPT)
	num  target     prot opt source               destination 

**插入规则**

	[root@bogon etc]# iptables -I INPUT -s 192.168.1.13 -j DROP
	[root@bogon etc]# iptables
	iptables v1.4.7: no command specified
	Try `iptables -h' or 'iptables --help' for more information.
	[root@bogon etc]# iptables -L
	Chain INPUT (policy DROP)
	target     prot opt source               destination         
	DROP       all  --  192.168.1.13         anywhere        插入到了最前边        
	ACCEPT     all  --  192.168.1.1          anywhere            
	DROP       all  --  anywhere             anywhere 

**请求服务要先将服务启动，如网站请求**

	[root@bogon ~]# iptables -A INPUT -p tcp --dport 80 -j ACCEPT
	[root@bogon ~]# iptables -P INPUT DROP

	Chain INPUT (policy DROP)
	target     prot opt source               destination         
	ACCEPT     all  --  192.168.15.1         anywhere            
	ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http 


**[root@bogon ~]# iptables -A INPUT -i eth0 -j ACCEPT**  进入到第一块网卡的数据接收

	[root@bogon ~]# iptables -A INPUT -i eth0 -j DROP
	[root@bogon ~]# iptables -I INPUT -i eth0 -j ACCEPT

	[root@bogon ~]# iptables -A OUTPUT -j DROP  这样客户端也不能接收到数据
	[root@bogon ~]# iptables -I OUTPUT -j ACCEPT

[root@bogon ~]# iptables -A OUTPUT -o eth0 -j DROP  -o指定数据包出去的网卡

**[root@bogon ~]# iptables -A OUTPUT -p tcp --sport 80 -j DROP**  出数据包协议和源端口

## 链接ssh ##
	
	[root@bogon ~]# ssh daiyan9095@192.168.15.129
	reverse mapping checking getaddrinfo for bogon [192.168.15.129] failed - POSSIBLE BREAK-IN ATTEMPT!
	daiyan9095@192.168.15.129's password: 
	Last login: Tue Jun 21 16:57:49 2016 from 192.168.15.129

**ping 命令使用的是icmp协议，这个比tcp快，禁止所有对服务器的ping，则设置以下命令**

	[root@bogon ~]# iptables -A INPUT -p icmp -j DROP
	[root@bogon ~]# ping 192.168.15.129
	PING 192.168.15.129 (192.168.15.129) 56(84) bytes of data.
	^C
	--- 192.168.15.129 ping statistics ---
	65 packets transmitted, 0 received, 100% packet loss, time 64782ms   丢失率100%

**只允许某个ip可以ping**

	[root@bogon ~]# iptables -I INPUT -s 192.168.15.129 -p icmp -j ACCEPT
	[root@bogon ~]# ping 192.168.15.129  可以ping的通
	PING 192.168.15.129 (192.168.15.129) 56(84) bytes of data.
	64 bytes from 192.168.15.129: icmp_seq=1 ttl=64 time=0.027 ms
	64 bytes from 192.168.15.129: icmp_seq=2 ttl=64 time=0.067 ms
	64 bytes from 192.168.15.129: icmp_seq=3 ttl=64 time=0.069 ms
	64 bytes from 192.168.15.129: icmp_seq=4 ttl=64 time=0.068 ms
	^C
	--- 192.168.15.129 ping statistics ---
	4 packets transmitted, 4 received, 0% packet loss, time 3344ms
	rtt min/avg/max/mdev = 0.027/0.057/0.069/0.020 ms

使用cmd  则ping不同，因为ip不在指定的里面

	C:\Users\Administrator>ping 192.168.15.129
	192.168.15.129 的 Ping 统计信息:
	    数据包: 已发送 = 4，已接收 = 0，丢失 = 4 (100% 丢失)，
	正在 Ping 192.168.15.129 具有 32 字节的数据:
	请求超时。

**保存防火墙设置，下次启动服务器时设置已经保存，否则只是在内存中**

	[root@bogon ~]# service iptables save  有些服务器可能没有这个命令
	iptables: Saving firewall rules to /etc/sysconfig/iptables:[  OK  ]
	
	[root@bogon ~]# vim /etc/sysconfig/iptables 在这里也可以直接编辑

打印设置的字符串

	[root@bogon ~]# iptables-save
	# Generated by iptables-save v1.4.7 on Tue Jun 21 20:22:26 2016
	*filter
	:INPUT ACCEPT [18:9463]
	:FORWARD ACCEPT [0:0]
	:OUTPUT ACCEPT [19:1339]
	COMMIT
	# Completed on Tue Jun 21 20:22:26 2016

可以将这个打印结果重定向到配置文件

	[root@bogon ~]# iptables-save >/etc/sysconfig/iptables  也可以

编辑防火墙规则：其他服务按照这个规则加上 如mysql svn vsftp 等

	  1 IPT="/sbin/iptables"
	  2 $IPT -F
	  3 $IPT -P INPUT DROP
	  4 $IPT -P FORWARD DROP
	  5 $IPT -P OUTPUT DROP
	  6 
	  7 $IPT -A INPUT -i lo -j ACCEPT
	  8 $IPT -A INPUT -p tcp --dport 80 -j ACCEPT
	  9 $IPT -A INPUT -p icmp -j ACCEPT 
	 10 $IPT -A INPUT -p tcp --dport 22 -j ACCEPT
	 11 
	 12 $IPT -A OUTPUT -o lo -j ACCEPT
	 13 $IPT -A OUTPUT -p tcp --sport 80 -j ACCEPT
	 14 $IPT -A OUTPUT -p icmp -j ACCEPT
	 15 $IPT -A OUTPUT -p tcp --sport 22 -j ACCEPT
	 16 
	 17 service iptables save
	 18 service iptables restart

**执行了编辑的文件**

	[root@bogon www]# ./iptables-set.txt 
	
	iptables: Saving firewall rules to /etc/sysconfig/iptables:[  OK  ]
	iptables: Setting chains to policy ACCEPT: filter          [  OK  ]
	iptables: Flushing firewall rules:                         [  OK  ]
	iptables: Unloading modules:                               [  OK  ]
	iptables: Applying firewall rules:                         [  OK  ]
	
	[root@bogon www]# iptables -L

**output要和-o一起用，不能喝-i一起用**

#48  apache 

apache  web服务器端程序

iptables stop 关闭防火墙与iptables -F 直接改配置文件不同

###LAMP  环境安装

##Apache
yum search apache 
yum -y install httpd 
和 httpd-devel

##mysql
yum search mysql 
yum -y install mysql 
yum -y install mysql-server 
yum -y install mysql-devel 
 
 ###php
 yum search php 
 yum -y install php 
 yum -y install php-devel
 yum -y install php-mysql 
 yum -y install php-gd
 yum -y install php-pdo 等等,看需要安装


设置apache开机启动
[root@bogon www]# chkconfig --level 35 httpd  on

[root@bogon www]# apachectl start  立即启动
[root@bogon www]# apachectl stop   立即关闭

[root@bogon www]# /etc/init.d/httpd start  绝对命令格式
[root@bogon www]# /etc/init.d/httpd stop

[root@bogon www]# service httpd start  服务格式
[root@bogon www]# service httpd stop  服务格式


[root@bogon www]# yum erase httpd  卸载


配置文件：
一般放在/etc下的软件名下，然后conf 下的软件名.conf
/etc/httpd/conf/httpd.conf  ---apace的配置主文件
[root@bogon httpd]# ls
conf  conf.d  logs  modules  run
conf是主配置文件，conf.d是配置文件的扩展 
建议将修改写在conf.d中，不要对conf进行修改
改变了主配置文件要重启

44 ServerTokens OS  能访问操作系统，显示系统信息

 536 ServerSignature On   表示显示服务器详细信息，改为Off则不显示，改为email则显示管理员邮箱
以上对应浏览器中：
Not Found

The requested URL /abc.php was not found on this server.

Apache/2.2.15 (CentOS) Server at 192.168.15.129 Port 80

 262 ServerAdmin root@localhost   设置管理员的邮箱

 57 ServerRoot "/etc/httpd"  文件根目录

  70 Timeout 60   指定连接的超时时间
   
76 KeepAlive Off   指定是否开启持续性链接

  83 MaxKeepAliveRequests 100   一次链接最大持续连接数

  89 KeepAliveTimeout 15  保持链接不操作最长时间

 136 Listen 80  监听80端口

 221 Include conf.d/*.conf  加载其他的配置项，包含文件

 242 User apache  apache的用户
 243 Group apache  apache用户的所属组

 277 ServerName localhost:80   填写网站的名称，如果一台服务器只服务一个网站，否则用虚拟机进行配置

  292 DocumentRoot "/var/www/html"   网站根目录

   302 <Directory />   跟目录的配置项
 303     Options FollowSymLinks   是否允许在根目录下创建软连接
 304     AllowOverride None      
 305 </Directory>

 343     Order allow,deny 设置那些人可以访问这个站 不能访问
 344     Allow from all  允许所有人可以访问

 402 DirectoryIndex index.html index.html.var   目录的默认文件，前面的优先级高

  366     UserDir disabled   是否可以访问网站的家目录

错误页面在apache端的设置
832 #ErrorDocument 500 "The server made a boo boo."
 833 #ErrorDocument 404 /missing.html
 834 #ErrorDocument 404 "/cgi-bin/missing_handler.pl"
 835 #ErrorDocument 402 http://www.example.com/subscription_info.html

ErrorDocument 404 /404.html   设置404页面
[root@bogon conf]# vim /var/www/html/404.html

虚拟主机：
服务器中放置很多网站，但速度会变慢

配置虚拟主机 配置文件中，在conf.d文件夹里修改更好
1003 #<VirtualHost *:80>
1004 #    ServerAdmin webmaster@dummy-host.example.com
1005 #    DocumentRoot /www/docs/dummy-host.example.com
1006 #    ServerName dummy-host.example.com
1007 #    ErrorLog logs/dummy-host.example.com-error_log
1008 #    CustomLog logs/dummy-host.example.com-access_log common
1009 #</VirtualHost>

[root@bogon conf.d]# ls
mod_dnssd.conf  php.conf  README  welcome.conf
[root@bogon conf.d]# vim virtual.conf  在conf.d文件夹下建立一个虚拟主机的配置文件 

<VirtualHost *:80>
    ServerAdmin daiyan10010@gmail.com   管理员邮箱
    DocumentRoot /var/www/blog    可访问的目录
    ServerName blog.hd.com    域名
      ErrorLog logs/blog.hd.com-error_log   错误日志
    CustomLog logs/blog.hd.com-access_log common
</VirtualHost>

<VirtualHost *:80>
    ServerAdmin daiyan10010@gmail.com   管理员邮箱
    DocumentRoot /var/www/bbs    可访问的目录
    ServerName bbs.hd.com    域名
      ErrorLog logs/bbs.hd.com-error_log   错误日志
    CustomLog logs/bbs.hd.com-access_log common
</VirtualHost>

出错的话要设置，表示按照名称来选择，否则只按照*80来选择，这会疑惑，因为都是*80
990 NameVirtualHost *:80


#49 rewrite重写

伪静态：1、可以将网站的重要信息隐藏起来
       2、防盗链

	http://localhost/index.php?c=index&nid=1
	转换为
	http://localhost/news_1.html 

**vim /etc/httpd/conf/httpd.conf**
配置文件中该项之前没有#号说明已经启用了该模块

	190 LoadModule rewrite_module modules/mod_rewrite.so


**htaccess文件也可以实现很多的作用**

	[root@localhost html]# ls -a
	.  ..  .htaccess  news.php
	[root@localhost html]#

**vim .htaccess**

	RewriteEngine On
	RewriteRule ^(\d+)\.html$ news.php?nid=$1 [L]

**编写virtualhost**

**[root@localhost conf.d]# vim virtual.conf**

	<VirtualHost *:80>
	    ServerAdmin daiyan_ms@hotmail.com
	    DocumentRoot /var/www/html
	    ServerName 192.168.15.129
	    ErrorLog logs/error_log
	    CustomLog logs/access_log common
	<Directory "/var/www/html">
	    Options FollowSymLinks
	    AllowOverride all
	</Directory>
	
	</VirtualHost>

**此时 在浏览器输入 192.168.15.129/1.html 访问的就是192.168.15.129/news.php?nid=1**

**在htaccess**

	RewriteRule \.(jpg|png|jpeg|gif|bml)$ noimg.html
使得所有访问本网图片访问noimg.html

在浏览器输入：http://192.168.15.129/1.png，访问的是noimg.html里的内容

**注释掉之前写的规则，设置404页面：**

	RewriteEngine On
	#RewriteRule ^(\d+)\.html$ news.php?nid=$1 [L]
	#RewriteRule \.(jpg|png|jpeg|gif|bml)$ noimg.html
	RewriteCond %{REQUEST_FILENAME} !-f 404.html
	RewriteCond %{REQUEST_FILENAME} !-d 404.html
	RewriteRule .? 404.html  [L]

RewriteCond 是条件
%{}这个是apache rewrite变量的引用方法

**设置图片防盗链**

	RewriteCond ${HTTP_REFERER} !^$
	RewriteCond ${HTTP_REFERER} !^http://192.168.15.129
	RewriteRule \.(jpg|png|jpeg|gif|bml)$ noimg.html



#57 FTP

文件传输协议

FTP的端口：20 21

- 端口20：传输数据
- 端口21：发布命令，建立命令

##主动模式和被动模式

###主动模式
1. 客户端随机开启一个大于1024的端口与服务器端的21端口进行连接
2. 客户端监听这个大于1024端口与服务器端口的链接
2. 服务器端通过20端口向客户端这个端口发送数据


###被动模式
1. 客户端开两个端口，大于1024，第一个端口与服务器端的21端口通信，传输命令
2. 客户端通过开启的另一个端口主动向服务器端请求数据
3. 服务器端随机开一个端口大于1024，来响应客户端的链接

###VSFTP  
1. 基于GPL
2. 快速
3. 非常安全基于ssh
4. redhat测试单台服务器支持15000个连接

安装前先去掉或者配置防火墙

**安装**

	yum install vsftpd

**启动**

	[root@bogon daiyan9095]# /etc/init.d/vsftpd start
	Starting vsftpd for vsftpd:                                [  OK  ]

设置开机启动项

	[root@bogon daiyan9095]# chkconfig --level 35 vsftpd on

linux下直接选择place-》链接-》ftp登录链接-》输入地址和用户名-》然后输入密码即可链接

win下需要软件filezilla  即可链接


	[root@bogon etc]# cd vsftpd/
	[root@bogon vsftpd]# ls
	ftpusers  user_list  vsftpd.conf  vsftpd_conf_migrate.sh
	[root@bogon vsftpd]# vim ftpusers

**这个文件显示的是不能通过vsftp登录服务器的用户名**

	# Users that are not allowed to login via ftp
	root
	bin
	daemon
	adm
	lp
	sync
	shutdown
	halt
	mail
	news
	uucp
	operator
	games
	nobody
	~

[root@bogon vsftpd]# vim user_list
这个文件也是控制哪些用户不能登录服务器，哪些用户能够登录服务器

这个文件的默认值可以在`vsftpd.conf`文件中更改

如果设置了匿名账号也可以登录则只能访问一下目录，而且该目录中的文件只能看下载，不能修改和删除

匿名账号是否登录可以在vsftp.conf里设置`anonymous_enable=YES`
，也可以在里面设置是否允许匿名账号写入和更改

	[root@bogon var]# cd ftp
	[root@bogon ftp]# ls
	pub
	[root@bogon ftp]# cd pub

anonymous_enable=NO关闭匿名账户访问权限

**设置权限**

默认情况下除了匿名账户不可以切换目录

	#chroot_local_user=YES   用户可以切换目录
	#chroot_list_enable=YES  
	# (default follows)
	#chroot_list_file=/etc/vsftpd/chroot_list  在这个文件里的用户可以切换目录，这个文件可能需要新建

**设置切换权限**

	chroot_local_user=YES
	chroot_list_enable=YES
	# (default follows)
	chroot_list_file=/etc/vsftpd/chroot_list

编辑chroot_list，增加daiyan9095,从而daiyan9095可以切换，而qq则不能切换了，只能操作自己的家目录

配置完要重启

	[root@bogon vsftpd]# service vsftpd restart
	Shutting down vsftpd:                                      [  OK  ]
	Starting vsftpd for vsftpd:                                [  OK  ]



#60 NTP

ntp时间同步

硬件时钟和软件时钟

date出的结果是软件时钟

date -s 22:20 设置时间

	[root@bogon vsftpd]# hwclock -r  读取硬件时钟
	Thu 30 Jun 2016 07:27:17 PM PDT  -0.437220 seconds

[root@bogon vsftpd]# hwclock -s  将硬件时钟同步到软件时钟，指软件时钟设置为硬件时钟的时间

	[root@bogon vsftpd]# date
	Thu Jun 30 19:29:07 PDT 2016

[root@bogon vsftpd]# hwclock -w  将软件时钟写到硬件时钟，与上面的相反



**ntp就是同步硬件和软件时钟，使他们一致，方法是找到一个服务器，每个一定时间来校准，将软件时钟写到硬件时钟**


- 安装ntp，可能已经安装 
		
		[root@bogon www]# rpm -qa ntp
		ntp-4.2.6p5-10.el6.centos.1.x86_64

- 启动ntpd服务

		[root@bogon www]# service ntpd start
		Starting ntpd:                                             [  OK  ]



vim  /etc/ntp.conf 这个文件中有同步时间的参考服务器

	server 0.centos.pool.ntp.org iburst
	server 1.centos.pool.ntp.org iburst
	server 2.centos.pool.ntp.org iburst
	server 3.centos.pool.ntp.org iburst

###同步时间：

**修改时间**

	[root@bogon etc]# date -s 22:10:23
	Thu Jun 30 22:10:23 PDT 2016
	[root@bogon etc]# date
	Thu Jun 30 22:10:25 PDT 2016


[root@bogon etc]# which ntpdate
/usr/sbin/ntpdate
[root@bogon etc]# /usr/sbin/ntpdate server 0.centos.pool.ntp.org iburst

**查看已经连接的ntp服务器地址**
	
	[root@bogon etc]# ntpq -p
	     remote           refid      st t when poll reach   delay   offse                                                    t  jitter
	=====================================================================                                                    =========
	 time4.aliyun.co 10.137.38.86     2 u 4971   64  177   42.205  -88823                                                    6 7507118
	 time7.aliyun.co 10.137.38.86     2 u 4971   64  177   31.846  -88823                                                    7 7507125
	 202.118.1.130   .STEP.          16 u    -   64    0    0.000    0.00                                                    0   0.000

crontab -e编辑计划

*/15 每个15分钟


#61 iptables 高级用法

**yum实际是下载和rpm包安装两个动作的结合**




































l代表是软连接
[root@bogon httpd]# ll
total 8
drwxr-xr-x. 2 root root 4096 Jun 21 23:13 conf
drwxr-xr-x. 2 root root 4096 Jun 18 20:48 conf.d
lrwxrwxrwx. 1 root root   19 Jun 13 15:19 logs -> ../../var/log/httpd
lrwxrwxrwx. 1 root root   29 Jun 13 15:19 modules -> ../../usr/lib64/httpd/modules
lrwxrwxrwx. 1 root root   19 Jun 13 15:19 run -> ../../var/run/httpd

[root@bogon httpd]# cd run
[root@bogon run]# ls
httpd.pid
[root@bogon run]# ll
total 4
-rw-r--r--. 1 root root 5 Jun 21 22:35 httpd.pid
[root@bogon run]# cat httpd.pid  主进程
3130
与下面的对应上了
[root@bogon run]# ps aux|grep httpd
root       3130  0.0  1.1 280008 11740 ?        Ss   20:46   0:00 /usr/sbin/httpd -k start
apache     4014  0.0  0.7 280008  7380 ?        S    22:35   0:00 /usr/sbin/http








apache是以模块化来进行的

[root@bogon httpd]# cd /etc/httpd/modules/ 这一个文件夹下的文件都为apache的模块
模块可以随意的安装和卸载

apache的日志
[root@bogon httpd]# cd /var/log/httpd/
[root@bogon httpd]# ls
access_log  error_log

access_log记录请求信息
  1 ::1 - - [18/Jun/2016:20:45:37 -0700] "GET / HTTP/1.1" 403 4961 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:45.0) Gecko/20100101 Firefox/45.0"
  2 ::1 - - [18/Jun/2016:20:45:37 -0700] "GET /icons/apache_pb.gif HTTP/1.1" 200 2326 "http://localhost/" "Mozilla/5.0 (X11; Linux x86_64; rv:45.0) Gecko/20100101 Firef    ox/45.0"
  3 ::1 - - [18/Jun/2016:20:45:37 -0700] "GET /icons/poweredby.png HTTP/1.1" 200 3956 "http://localhost/" "Mozilla/5.0 (X11; Linux x86_64; rv:45.0) Gecko/20100101 Firef    ox/45.0"
 23 192.168.15.1 - - [20/Jun/2016:20:17:08 -0700] "GET /favicon.ico HTTP/1.1" 404 289 "-" "Mozilla/5.0 (Windows NT 10.0; WOW64; rv:47.0) Gecko/20100101 Firefox/47.0"
 24 192.168.15.1 - - [20/Jun/2016:20:17:08 -0700] "GET /favicon.ico HTTP/1.1" 404 289 "-" "Mozilla/5.0 (Windows NT 10.0; WOW64; rv:47.0) Gecko/20100101 Firefox/47.0"
 25 192.168.15.1 - - [20/Jun/2016:20:23:16 -0700] "GET / HTTP/1.1" 200 1112 "-" "Mozilla/5.0 (Windows NT 10.0; WOW64; rv:47.0) Gecko/20100101 Firefox/47.0"
 26 192.168.15.1 - - [21/Jun/2016:17:45:26 -0700] "GET / HTTP/1.1" 200 1112 "-" "Microsoft Windows Network Diagnostics"
 27 192.168.15.1 - - [21/Jun/2016:17:45:28 -0700] "GET / HTTP/1.1" 200 1112 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome    /51.0.2704.84 Safari/537.36"


error_log记录连接的错误信息
  1 [Sat Jun 18 20:41:55 2016] [notice] SELinux policy enabled; httpd running as context unconfined_u:system_r:httpd_t:s0
  2 [Sat Jun 18 20:41:55 2016] [notice] suEXEC mechanism enabled (wrapper: /usr/sbin/suexec)
  3 [Sat Jun 18 20:41:56 2016] [notice] Digest: generating secret for digest authentication ...
  4 [Sat Jun 18 20:41:56 2016] [notice] Digest: done
  5 [Sat Jun 18 20:41:56 2016] [warn] ./mod_dnssd.c: No services found to register


请求了一个不存的文件abc.php
 [root@bogon httpd]# tail -1 error_log 
[Tue Jun 21 23:03:12 2016] [error] [client 192.168.15.1] script '/var/www/html/abc.php' not found or unable to stat




#63  linux桌面版 
ubuntu 软件包与centos 的不同 

ubuntu 的是apache2 
实际安装可以将系统光盘镜像写入到u盘中

apt-cache seatch mysql  搜索mysql源

apt-get install  mysql  安装mysql 

ubuntu下用户都可以sudo,ubunt默认不可以切换root,需要设置个密码sudo passwd root 

安装netbeans  开发ide

安装apache2 
linux-ubuntu@ubuntu:~$ sudo apt-cache search apache 
重启或启动
linux-ubuntu@ubuntu:~$ sudo apachectl restart

linux-ubuntu@ubuntu:/etc/apache2$ sudo mysql
linux-ubuntu@ubuntu:/etc/apache2$ sudo apt-get install php5 php5-mysql php5-gd
linux-ubuntu@ubuntu:/etc/apache2$ sudo apachectl restart  安装完要重启

安装netbeans 
linux-ubuntu@ubuntu:~/下载$ sudo chmod 0777 netbeans-8.1-php-linux-x64.sh 
linux-ubuntu@ubuntu:~/下载$ ll
总用量 132108
drwxr-xr-x  2 linux-ubuntu linux-ubuntu      4096  6月 22 21:24 ./
drwxr-xr-x 22 linux-ubuntu linux-ubuntu      4096  6月 22 21:19 ../
-rwxrwxrwx  1 linux-ubuntu linux-ubuntu 116597760  6月 22 20:49 netbeans-8.1-php-linux-x64.sh*
-rw-rw-r--  1 linux-ubuntu linux-ubuntu  18665332  6月 22 21:24 sogoupinyin_2.0.0.0078_amd64.deb
linux-ubuntu@ubuntu:~/下载$ ./netbeans-8.1-php-linux-x64.sh


启动netbeans 
linux-ubuntu@ubuntu:~/netbeans-8.1$ cd bin 
linux-ubuntu@ubuntu:~/netbeans-8.1/bin$ ls
jre  netbeans  netbeans64.exe  netbeans.exe
linux-ubuntu@ubuntu:~/netbeans-8.1/bin$ ./netbeans

给netbeans 创建软连接


#安装lamp


[centos@bogon Desktop]$ rpm -q make   查询是否安装了某包

[root@bogon html]# rpm -q gcc

[centos@bogon tmp]$ rpm -q gcc-c++
package gcc-c++ is not installed


C:\Users\Administrator>mysql -h 192.168.15.129 -uroot -p  远程登录mysql,-h指定ip


=======================================================
#Apache

##apache安装和文件

yum list | grep httpd

service httpd stop

service httpd start

service httpd restart

service httpd graceful---优雅的重启，不会终止用户的连接

service httpd graceful-stop  优雅的关闭，处理完所有的请求后关闭

chkconfig --level 35 httpd on

配置文件：/etc/httpd

主配置文件目录：conf/httpd.conf

模块配置文件目录 conf.d/

日志文件：连接到 /var/log

模块:modules/

run/  运行时的一些信息，连接到 /var/run/httpd

默认网站根目录：/var/www

默认网站网页目录：/var/www/html

新的用户apache nologin

##apache的工作原理和基本概念

###apaceh 的进程
默认监听80端口

apache会启动一个主进程（控制进程），主进程会开启多个子进程

主进程以root身份运行，子进程以apache用户开启

ps aux | grep httpd

查看模块：httpd M

	[root@localhost daiyan9095]# httpd -M
	Loaded Modules:
	 core_module (static)-----静态模块
	 mpm_prefork_module (static)
	 http_module (static)
	 so_module (static)
	 auth_basic_module (shared)----动态加载模块
	 auth_digest_module (shared)
	 authn_file_module (shared)
	 authn_alias_module (shared)
	 authn_anon_module (shared)

查看静态编译入程序的模块：httpd -l

	Compiled in modules:
	  core.c
	  prefork.c
	  http_core.c
	  mod_so.c

##进程管理

MPM机制

[root@localhost daiyan9095]# httpd -V  查看MPM管理器
Server version: Apache/2.2.15 (Unix)
Server built:   May 11 2016 19:28:33
Server's Module Magic Number: 20051115:25
Server loaded:  APR 1.3.9, APR-Util 1.3.9
Compiled using: APR 1.3.9, APR-Util 1.3.9
Architecture:   64-bit
Server MPM:     Prefork -----为Prefork
  threaded:     no

每个子进程在每一个时间点只能处理一个请求

##Apache进程

主配置文件：

	# prefork MPM
	# StartServers: number of server processes to start
	# MinSpareServers: minimum number of server processes which are kept spare
	# MaxSpareServers: maximum number of server processes which are kept spare
	# ServerLimit: maximum value for MaxClients for the lifetime of the server
	# MaxClients: maximum number of server processes allowed to start
	# MaxRequestsPerChild: maximum number of requests a server process serves
	<IfModule prefork.c>
	StartServers       8   服务启动时默认启动8个子进程
	MinSpareServers    5   最小空闲进程数量
	MaxSpareServers   20	最大空闲进程数量
	ServerLimit      256   限制下面的值，为下面值的上限
	MaxClients       256    最大处理并发量
	MaxRequestsPerChild  4000   每个子进程能够处理的请求数量，超过了就杀掉在创建新的进程
	</IfModule>

**每个1秒查看httpd的进程**

[root@localhost daiyan9095]# watch -n 1 'ps uax | grep httpd'

**压力测试**

[daiyan9095@localhost ~]$ ab -c 16 -n 10000 http://192.168.15.129/index.php


##Apache主配置文件

### Section 1: Global Environment
全局配置，适用于整个网站

	ServerTokens OS  当查找不到文件时，显示系统的信息，这个影响这个信息的详细程度
	如：Apache/2.2.15 (CentOS) Server at 192.168.15.129 Port 80
	可选值：FULL和MAJOR和OS  

	ServerRoot "/etc/httpd"
	控制配置文件的主目录

	PidFile run/httpd.pid
	控制主进程的进程ID，这是一个相对路径，绝对为ServerROOT+这个目录

	Timeout 60
	指定apache接受服务的超时时间

	KeepAlive Off
	tcp请求是否可以保持

	MaxKeepAliveRequests 100
	打开keepalive的情况下一个tcp连接最多请求的数量

	KeepAliveTimeout 15
	一个tcp连接两次请求之间的最长时间间隔

	Listen 80
	服务默认监听的端口号

	Include conf.d/*.conf
	加载额外的配置文件，结尾是.conf的文件都会加载

	User apache
	Group apache
	指定apache的子进程用户和组



### Section 2: 'Main' server configuration

主服务配置，默认站点配置，根目录为/var/www/
	
	
		ServerAdmin root@localhost
	指定管理员的邮箱，500错误等时会提示在浏览器上
	
	ServerName localhost:80
	指定网站的域名
	
	UseCanonicalName Off
	指定是否使用一个严格合法的站点，严格方式必须为http://www.XXX
	
	DocumentRoot "/var/www/html"
	网站目录
	
	<Directory />
	    Options FollowSymLinks
	    AllowOverride None
	</Directory>
	指定对指定的目录的访问控制，这里是根目录，配置的是缺省的访问控制
	
	<Directory "/var/www/html">
	    Order allow,deny
	    Allow from all
	
	</Directory>
	直接配置网站根目录的访问配置
	
	   
	
	
	<IfModule mod_userdir.c>
	...
	 #UserDir public_html

	</IfModule>
	条件化的配置加载，如果加载了指定模块则应用规则
	
	DirectoryIndex index.html index.html.var
	不指定文件时默认访问的文件，依次判断
	
	AccessFileName .htaccess
	加载访问控制的配置文件，注意这里相对的路径是section 2指定根目录
	
	<Files ~ "^\.ht">
	    Order allow,deny
	    Deny from all
	    Satisfy All
	</Files>
	对文件访问进行控制
	
	TypesConfig /etc/mime.types
	指定MIME配置文件的路径
	
	DefaultType text/plain
	指定网页默认的类型，为纯文本
	
	HostnameLookups Off
	是否进行域名的解析，非常占资源缓慢
	
	ErrorLog logs/error_log
	默认服务器错误日志路径
	
	LogLevel warn
	错误日志的详细程度，依次递减
	
	LogFormat "%{Referer}i -> %U" referer
	LogFormat "%{User-agent}i" agent
	....
	日志格式
	
	ServerSignature On
	服务器签名，是否显示服务器详细信息
	
	Alias /icons/ "/var/www/icons/"
	别名配置，浏览器输入地址简化
	
	ScriptAlias /cgi-bin/ "/var/www/cgi-bin/"
	脚本的别名
	
	AddDefaultCharset UTF-8
	指定网页默认编码
	
	BrowserMatch "RealPlayer 4\.0" force-response-1.0
	BrowserMatch "Java/1\.0" force-response-1.0
	BrowserMatch "JDK/1\.0" force-response-1.0
	对不同的浏览器的个性化配置

### Section 3: Virtual Hosts
虚拟主机配置



#PHP Excel

为了简化浏览器地址栏输入，配置一个虚拟域名

1. d开启apche的rewrite重写模块

		#LoadModule rewrite_module modules/mod_rewrite.so
2.开启vhost
	
		# Virtual hosts
		#Include conf/extra/httpd-vhosts.conf
3. 在上面说明情况下编辑httpd-vhosts.conf文件

		#配置操作phpexcel时的虚拟域名
		NameVirtualHost *:80
		<VirtualHost *:80>
		    ServerAdmin webmaster@dummy-host2.example.com
		    DocumentRoot "D:/wamp/www/phpexcel"
		    ServerName www.phpexcel.com
		    #ErrorLog "logs/dummy-host2.example.com-error.log"
		    #CustomLog "logs/dummy-host2.example.com-access.log" common
		</VirtualHost>
		<Directory "D:/wamp/www/phpexcel">
		    Options Indexes FollowSymLinks
		    AllowOverride None
		    Order deny,allow
		    Allow from all
		</Directory>
4. 修改hosts文件，添加一行

		127.0.0.1 www.phpexcel.com

**在浏览器输入www.phpexcel.com即访问的是我们指定的工作目录D:/wamp/www/phpexcel**

**检测类：**

	include './phpexcel/phpexcel/PHPExcel.php';

	$PHPExcel=new PHPExcel();
	print_r($PHPExcel);