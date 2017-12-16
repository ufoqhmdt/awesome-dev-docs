# Linux 常用命令记录

``` sudo apt-get install -y python-software-properties software-properties-common; ```
```sudo apt-get install build-essential python-dev libevent-dev python-pip liblzma-dev```
```sudo apt-get install g++ flex bison gperf ruby perl \```
```libsqlite3-dev libfontconfig1-dev libicu-dev libfreetype6 libssl-dev \```
```libpng-dev libjpeg-dev```

superputty
putty-tunnel-manager


`chgrd` 修改组.
lsmod 内核模块
modprobe  加载一个模块到内核
runlevel 查看运行级别
cd - #回最近一次的路径


startx -- :1 #启动第二个xwindow
startx -- :2 #启动第三个xwindow
id #查看自己信息
touch `date +%m%d`.log #
file  filename 

exit #退出当前shell
logout #退出登录shell
关机:
* shutdown -h now
* init 0
* halt -p -f
* poweroff
重启:
* shutdown -r now
* init 6
* reboot

kill -l #查看信号量
stty -a #To get all the terminal control character assignlments:
Ubuntu下轻松切换GDM, LightDM , KDM: sudo dpkg-reconfigure gdm

 
装机必装:
* mongodb
* ipython
* traceroute
* nodejs
* mtr
* tree
* curl
* pstree
* nginx
* 
$? 记录命令的退出状态,0是成功 ,非0 失败
$#
 
 
1. 在终端下：
        复制命令：Ctrl + Shift + C  组合键.
        粘贴命令：Ctrl + Shift + V  组合键. 
2. 在控制台下：
        复制命令：Ctrl + Insert  组合键 或 用鼠标选中即是复制。
        粘贴命令：Shift + Insert  组合键 或 单击鼠标滚轮即为粘贴。

Ctrl + a 可以快速切换到命令行开始处
Ctrl + e 切换到命令行末尾
Ctrl + r 在历史命令中查找
Ctrl-x-e 在编辑器中工作

删除光标所在位置之前的所有字符：Ctrl + u
删除光标所在位置之后的所有字符：Ctrl + k

Ctrl + c 终止命令（懂的人都知道，其实是发送SIGINT）信号到进程。
Ctrl + d 结束当前输入、退出shell
Ctrl + z 转入后台运行

!! 执行上一条执行过的命令
!$ 显示系统最近的一条命令的参数
最后这个比较有用，比如我先用cat /etc/mysql/my.cnf，然后我想用vi编辑。一般的做法是先用↑ 显示最后一条命令，然后用Ctrl + a 移动到命令最前，删除cat，然后再输入vi命令。
利用了上面的命令后，可以用vi !$来代替。

局域网下载超方便啊:
下面的命令生产一个通过HTTP显示文件夹结构树的简单网页，可以通过浏览器在端口8000访问，直到发出中断信号。

1
# python -m SimpleHTTPServer


* /dev/sd1 - /dev/sd4   #primary 只能有4个
* /dev/sd5 ......   #extend的有
 
uptime
lspci
last 查看登录信息.其实就是查看/var/log/wtmp文件.不过这个文件是特殊文件用cat是乱码.


-普通文件
d目录文件directory
l链接文件link
b区块设备block
c字符设备character
s资料接口文件sockets
f数据传输文件FIFO pipo first in first out.
 
\rm -r /tmp/etc # 在指令前加上反斜杠，可以忽略掉 alias 的指定选项喔！
mkdir -p a/b/c #批量建立文件夹


find -name *.a -exec rm {} \; #删除所有.a的文件
find -name \*[!.b] #找到所有不是.b的文件
find *[!.b] #找到所有不是.b的文件.不过结果没有.\ .这里可以配合上面的exec命令
rm *[!.b] #所有所有不是.b的文件
find * #
find -name \* #./

grep 'getunicode' conmakehash.c # 找文件里面的内容.
grep -R 'ufo' . # 在当前目录下面递归查找ufo

$ find . -name *.txt 
find: paths must precede expression
Usage: find [path...] [expression] 
$ find . -name "*.txt" #加上引号就没问题了.

Ubuntu server关机方式     
1. 启用高级电源管理
apt-get install acpid
2. 命令集
sudo init 0  
sudo init 6 #为重新启动
sudo shutdown -h now  
sudo poweroff #关闭  
sudo reboot #重启  
sudo shutdown -r now #重启  
#如果切换到root权下 直接输入命令 免sudo  
shutdown -h #是关机，最终是调用halt命令关机。
poweroff #只是做了磁盘同步就直接切断了电源，对于运行后台服务的服务器来说不太合适。
 
让所有www目录下的都有w权限.-R递归
sudo chmod a+w -R www/
将档案 file1.txt 设为所有人皆可读取 :
chmod a+r file1.txt
chmod ugo+r file1.txt
将档案 file1.txt 与 file2.txt 设为该档案拥有者，与其所属同一个群体者可写入，但其他以外的人则不可写入:
chmod ug+w,o-w file1.txt file2.txt 
 
以前用Redhat Enterprise Linux的时候，RH系统提供了chkconfig这个简单的命令来方便地管理系统在不同运行级别下的服务开启/关闭， chkconfig ServiceName on/off 并可以用chkconfig --list来查看当前的制定状况。 装了Ubuntu之后，没了这个命令我一直通过mv /etc/rcX.d（在这里X的取值是从0到6）下的启动脚本名来管理服务， 其实，Ubuntu也提供了另外一个简单的命令来实现管理。但首先服务必须已在/etc/init.d目录中存在。如： 添加一个服务: sudo update-rc.d ServiceName defaults 删除一个服务: sudo update-rc.d ServiceName remove 巨方便


/bin/false是最严格的禁止login选项，一切服务都不能用。而/sbin/nologin只是不允许login系统，但可以使用其他ftp等服务。如果想要用false在禁止login的同时允许ftp，则必须在/etc/shells里增加一行/bin/false.

比如:useradd -s /sbin/nologin ufo #这个用户就不能登录,比较安全,用于FTP等.

mount /dev/cdrom /mnt
mount -t iso9660 /dev/cdrom /mnt  #访问光盘
mount //192.168.0.2/ufo /mnt 
mount -t cifs //192.168.0.2/ufo  /mnt #访问windows共享 这里指定为CIFS.好像默认是sambafs
mount -t cifs -o username=adminstrator //192.168.0.2/ufo /mnt
mount 192.168.0.2:/var/ftp/pub /mnt  #访问linux共享  NFS

cat /dev/cdrom>ufo.iso #制作iso文件.方便啊
mount -t iso9660 -o loop a.iso /mnt #加载ISO文件

du -s ufo/ #查看文件夹ufo的大小.
用户名管理
useradd ufo 添加用户名
passwd ufo 修改密码
userdel ufo  删除ufo
userdel -r ufo 删除ufo及他的目录
id ufo查看
groupadd ufogroup添加组    /etc/group
useradd -g ufogroup ufo 把ufo加入ufogroup组   /etc/passwd
sudo gpasswd -a ufo docker #把ufo加入到docker组

usermod -d /home/newdict -m ufo #修改home目录
usermod -L ufo #冻结ufo.其实是在shadow文件加了!
usermod -U ufo#解冻

su #切换到root
su - #切换并初始化root环境.
sudoers文件ufo ALL=(ALL:ALL) NOPASSWD:ALL 表示ufo可以从任何地方登陆执行任何人的任何命名.还不用输入密码.
创建用户的时候，指定sudo组，这样用户就有sudo权限了。
如果没有sudo组，试试admin组。
sudo useradd -m -s /bin/bash -g sudo ufo
sudo passwd ufo
123456
123456
也可以用adduser.我个人更喜欢.
mon@csm:~$ sudo adduser ufo
Adding user `ufo' ...
Adding new group `ufo' (1002) ...
Adding new user `ufo' (1002) with group `ufo' ...
Creating home directory `/home/ufo' ...
Copying files from `/etc/skel' ...
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Changing the user information for ufo
Enter the new value, or press ENTER for the default
     Full Name []: ufo
     Room Number []:
     Work Phone []:
     Home Phone []:
     Other []:
Is the information correct? [Y/n] y
给老用户添加sudo权限
sudo usermod -g sudo ufo
还可以
添加文件的写权限。也就是输入命令"chmod u+w /etc/sudoers"。修改完了再去掉w权限.我不喜欢.
last  命令显示的是上次登录用户的历史信息。这个命令通过搜索文件“/var/log/wtmp”，显示logged-in和logged-out及其tty‘s的用户列表。
普通用户UID一般大于500,root UID是0.系统用户是系统运行时必须有的用户.比如apache,mysql.
id 查看自己的UID等信息
groups查看所属组


SAMBA

[ufo]
  path =/home/ufo
  read only = no
  browseable = yes
  writable = yes
  valid users = ufo
[var]
  path =/var
  read only = no
  browseable = yes
  writable = yes
  valid users = ufo

Linux下终端字体颜色设置方法


修改时区
1. cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
2. hwclock 
3. more /etc/timezone #查看时区
4. date -s 14:36:00 #手动修改时间.

运行级别
/etc/inittab的id:5:inidefault 把5改了就OK
但是Unbuntu里面没有了inittab,软件包已经被Upstart软件包替换了，所有的配置信息都在/etc/event.d/目录下.google.但是我发现event.d也没有啊?
apt安装sysv-rc-conf,可以改运行级别

基本文件操作
 
ls -ahl
nl file 可以在文件查看的时候加上行号.
ls | shuf -n1 (pick on random selection)  随机从一个文件或文件夹中选择行/文件/文件夹 -n2 随机两个.依次类推
tree 以树式的格式得到当前文件夹的结构。

挂载
mount /mnt/cdrom
unmount
 
环境变量
1、/etc/profile:在登录时,操作系统定制用户环境时使用的第一个文件,此文件为系统的每个用户设置环境信息,当用户第一次登录时,该文件被执行。
2、/etc/environment:在登录时操作系统使用的第二个文件,系统在读取你自己的profile前,设置环境文件的环境变量。
3、~/.bash_profile:在登录时用到的第三个文件是.profile文件,每个用户都可使用该文件输入专用于自己使用的shell信息,当用户登录时,该文件仅仅执行一次!默认情况下,他设置一些环境变量,执行用户的.bashrc文件。
/etc/bashrc:为每一个运行bash shell的用户执行此文件.当bash shell被打开时,该文件被读取.ubuntu我发现是/etc/bash.bashrc
4、~/.bashrc:该文件包含专用于你的bash shell的bash信息,当登录时以及每次打开新的shell时,该该文件被读取。
 
查看环境变量env
 
系统环境变量一般保存在下面的文件中：
* /etc/environment
* /etc/profile
* /etc/bash.bashrc
          /etc/profile和 /etc/bash.bashrc在Ubuntu 10.0版本中不推荐使用。
一般都是在profile里面加入 export PATH="$PATH:/my_new_path"
立即生效方法:$source /etc/profile
其他文件的修改方式与此类似，需要注意的是/etc/environment不需要使用export设置环境变量，其他profile文件需要。
需要注意的是，最好不要把当前路径”./”放到PATH里，这样可能会受到意想不到的攻击。
 
附加信息:
/etc/login.defs
 
修改shell
chsh -s /bin/bash
 
 
跳板机穿墙
chsh -s /bin/bash
ssh -f -i victor.key -L 0.0.0.0:50001:172.18.0.128:80 -L 0.0.0.0:50002:172.18.0.128:443 -L 0.0.0.0:50003:172.18.0.128:22 -L 0.0.0.0:50004:172.18.0.82:22
-o "ServerAliveInterval=10" i313452@jump-zone4.iaas.mo.sap.corp -N -vvv

#可以一次性开放多个端口.i313452@jump-zone4.iaas.mo.sap.corp是跳板机.这个跳板机必须是具有ssh的功能.无论他是不是22端口.比如我尝试使用公司的浏览器proxy的8080端口就无法出去.这个proxy一定是不具有ssh功能.
 
网络
tracert www.baidu.com可以追踪ip的网关.

redhat可以运行setup设置一些网络配置.

scp ufo@192.168.93.56:/home/ufo/.profile .   从192.168.93.56复制到我本地.
ss 表示socket统计。这个命令调查socket，显示类似netstat命令的信息。它可以比其他工具显示更多的TCP和状态信息。
那么如何得到你的外部IP地址呢？使用google？那么这个命令就在你的终端输出你的外部IP地址。

1
# curl ifconfig.me


查看公网IP 用这条命令可以 curl http://iframe.ip138.com/ic.asp 因为ifconfig好像不能看到公网地址.

crontab -e 添加
crontab -r 终止
crontab -l 列出当前的任务

chown -R root . 把当前目录下的所有文件好像还有子目录全部修改为root用户的

比如我要让mysql和apache开机启动
echo "/usr/local/apache2/bin/apachectl start">>/etc/rc.local
echo "/usr/local/mysql/bin/mysqld_safe --user=mysql &">>/etc/rc.local
 


 
apt-get install packagename  安装一个新软件包（参见下文的aptitude）
apt-get remove packagename  卸载一个已安装的软件包（保留配置文档）   
apt-get --purge remove packagename  卸载一个已安装的软件包（删除配置文档）
dpkg --force-all --purge packagename  有些软件很难卸载，而且还阻止了别的软件的应用，就能够用这个，但是有点冒险。
apt-get autoclean apt  会把已装或已卸的软件都备份在硬盘上，所以假如需要空间的话，能够让这个命令来删除您已删掉的软件
apt-get clean  这个命令会把安装的软件的备份也删除，但是这样不会影响软件的使用。
apt-get upgrade  更新任何已安装的软件包
apt-get dist-upgrade  将系统升级到新版本
apt-cache search string  在软件包列表中搜索字符串   
dpkg -l package-name-pattern  列出任何和模式相匹配的软件包。假如您不知道软件包的全名，您能够使用“*package-name-pattern*”。
aptitude  周详查看已安装或可用的软件包。和apt-get类似，aptitude能够通过命令行方式调用，但仅限于某些命令——最常见的有安装和卸载命令。由于aptitude比apt-get了解更多信息，能够说他更适合用来进行安装和卸载。
apt-cache showpkg pkg  显示软件包信息。   
apt-cache dumpavail  打印可用软件包列表。
apt-cache show pkg  显示软件包记录，类似于dpkg –print-avail。apt-cache pkgname  打印软件包列表中任何软件包的名称。
dpkg -S file  这个文档属于哪个已安装软件包。
dpkg -L package  列出软件包中的任何文档。   
apt-file search filename  查找包含特定文档的软件包（不一定是已安装的），这些文档的文档名中含有指定的字符串。apt-file是个单独的软件包。您必须先使用apt-get install来安装他，然後运行apt-file update。假如apt-file search filename输出的内容太多，您能够尝试使用apt-file search filename | grep -w filename（只显示指定字符串作为完整的单词出现在其中的那些文档名）或类似方法，例如：apt-file search filename | grep /bin/（只显示位于诸如/bin或/usr/bin这些文档夹中的文档，假如您要查找的是某个特定的执行文档的话，这样做是有帮助的）。  
apt-get autoclean  定期运行这个命令来清除那些已卸载的软件包的.deb文档。通过这种方式，您能够释放大量的磁盘空间。假如您的需求十分迫切，能够使用apt-get clean以释放更多空间。这个命令会将已安装软件包裹的.deb文档一并删除。大多数情况下您不会再用到这些.debs文档，因此假如您为磁盘空间不足而感到焦头烂额，这个办法也许值得一试。


apt-key是Debian软件包的安全管理工具。每个发布的deb包，都是通过密钥认证的，apt-key用来管理密钥。
apt-key list 列出已保存在系统中key。
apt-key add keyname 把下载的key添加到本地trusted数据库中。
apt-key del keyname 从本地trusted数据库删除key。
apt-key update 更新本地trusted数据库，删除过期没用的key。
apt-cache show gedit 查看是否安装gedit 不是apt-get.我忽视了dpkg -l | grep filename
dpkg -L filename
就能列出该软件的所有文件位置
另外，从新立得里也可以找到

 
除了使用history命令查看历史命令外，Linux系统还提供了非常灵活的Shell历史命令调用方法，我们可以在Shell命令提示符或者Shell脚本中使用它们：
　　!!　　　　前一条命令；
　　!:0 　　　不带参数的前一条命令名；
　　!^ 　　　前一条命令的第一个参数；
　　!:n 　　　前一条命令的第n个参数；
　　!$ 　　　 前一条命令的最后一个参数；
　　!* 　　　 前一条命令的所有参数，命令名除外；
　　!n 　　　 第n条命令；
　　!-n 　　　倒数第n条命令；
　　!str　　　 最近一条以str开头的命令；
　　!?str　 　 最近一条包含str的命令；
　　^a^b　　将上一条命令名中的a替换为b；
　　!:gs/a/b　将上一条命令的所有a替换为b（包含命令名和参数）。
软件安装 
dpkg方式(deb包)：
           安装: dpkg -i package.deb
移除式卸载：dpkg -r xxx
清除式卸载：dpkg -P xxx
 
1. 先安装 alien(并非完美转换) 和 fakeroot 这两个工具，其中前者可以将 rpm 包转换为 deb 包。安装命令为：
    sudo apt-get install alien fakeroot
2. 将需要安装的 rpm 包下载备用，假设为 package.rpm。
3. 使用 alien 将 rpm 包转换为 deb 包：
    fakeroot alien package.rpm
4. 一旦转换成功，我们可以即刻使用以下指令来安装：
    sudo dpkg -i package.deb
进程
查看进程树:pstree -p|grep mong
查看samba是否运行:pgrep smbd
查看内核版本命令：
1. cat /proc/version
2. uname -a
3. uname -r
查看linux版本：　　
* lsb_release -a #注:这个命令适用于所有的linux，包括Redhat、SuSE、Debian等发行版。
* cat /etc/issue
* cat /etc/redhat-release #注:这种方式下可以直接看到具体的版本号，比如 AS4 Update 1
* rpm -q redhat-release #注:这种方式下可看到一个所谓的release号，比如上边的例子是3这个release号和实际的版本之间存在一定的对应关系，如下：
　　redhat-release-3AS-1 -> Redhat Enterprise Linux AS 3
　　redhat-release-3AS-7.4 -> Redhat Enterprise Linux AS 3 Update 4
　　redhat-release-4AS-2 -> Redhat Enterprise Linux AS 4
　　redhat-release-4AS-2.4 -> Redhat Enterprise Linux AS 4 Update 1
　　redhat-release-4AS-3 -> Redhat Enterprise Linux AS 4 Update 2
　　redhat-release-4AS-4.1 -> Redhat Enterprise Linux AS 4 Update 3
　　redhat-release-4AS-5.5 -> Redhat Enterprise Linux AS 4 Update 4
　　另:第3)、4)两种方法只对Redhat Linux有效
查看自己的LINUX是多少位的
 
PS1="\[\033[1;32;1m\][\[\033[0;32;1m\]\u@\h:\[\033[1;35;1m\]\w\[\033[1;32;1m\]]\[\033[1;31;1m\]\$\[\033[1;32;1m\]"

* getconf WORD_BIT
* echo $HOSTTYPE
常用 shell 命令
   注：Linux 系统只乎全部命令都有 -h|--help 选项，如遇不记得某命令的选项，使用此选项随时查阅      注：Linux 系统只乎全部命令都有 -h|--help 选项，如遇不记得某命令的选项，使用此选项随时查阅    
        man 命令手册查看(Manual):
           此 man 非彼 man，放在第一个介绍，是因为掌握此命令，以下的命令应用就不那么费劲，在不了解某命
              令时，随时查阅其手册即可，相当于该命令的 -h|--help 选项，但信息或许更详细。
           注：若 man 命令查阅不出内容，可能需要安装 man-pages 包。
           man [选项] 命令
           man 命令常用选项：
                -k keyword      以 "keyword" 作为关键词搜索帮助手册
                 num            num 为具体 1~9 的数字。man 手册分类为 9 部分，
                                  深入了解可查看 man 命令手册(man man)
           用法示例：
                man -K printf
                man    printf
                man 3  printf

        type 描述命令类型
           type 是 Bash Shell 内建命令，不是独立程序。
           type 命令名
           用法示例：
                type mv
                type -p type    # -p 选项是显示命令路径

        whereis 定位命令的执行文件，源码以及手册页文件
           whereis [选项] 命令名, ...
           whereis 命令常用选项：
                -b              仅定位二进制文件
                -m              仅定位手册文件
                -s              仅定位源码文件
           用法示例：
                whereis mv      # 查找出有关 cp 命令的执行文件，源码及手册页位置

        cd 改变工作目录(Change working Direcotry)
           cd [目录路径]  # 如果省略 目录路径，则将进入到用户家目录。也是shell 内建命令
           用法示例：
                cd /tmp
                cd ~            # 进入用户家目录，在 bash shell 中，符号"~"表示用户家目录
                cd              # 省略路径，也进入用户家目录

        cp 文件复制(copy)
           cp [选项] 源文件 目标文件
           cp 命令常用选项：
                -r      递归复制，即复制整个目录
                -v      输出复制过程信息
                -i      若目标文件已经存在，默认操作将覆盖目标文件，此选项则请求用户确认
                -n      不复制已经存在的文件
                -u      只复制比目标文件更新的文件
           用法示例：
                cp    filesrc filedst       # 复制当前目录下 filesrc 文件成 filedst
                cp -r dirsrc  dirdst        # 复制当前目录下 dirsrc 目录 到 dirdst 目录

        mv 文件移动(move), 与文件复制命令 cp 相似，不同处是操作完成后源文件将被删除；需要留意：mv 命
             令没有递归选项 -r，移动目录跟移动普通文件没有区别
           mv [选项] 源文件 目标文件
           mv 命令常用选项:
                -i      默认情况下, mv 将覆盖掉源文件，此选项则请求用户确认
                -n      不移动已存在文件
                -u      只移动比目标文件更新的文件
                -v      显示详细移动过程
           用法示例：
                mv -vi file1 file2      # 交互式移动文件。该命令同目录下移动，实际是重命名文件

        touch 创建文本文件, 如果要创建的文件已经存在，则更新文件访问及修改时间为当前时间
           touch [选项] 文件名1 ...
           用法示例：
                touch file1     # 若 file1 文件未存在，则建立名为 file1 的文本文件，
                                # 否则更新其访问时间与修改时间

        file 文件类型查看：
           Linux 中不以文件后缀名区分文件，不清楚某一文件类型时，使用此命令即可判断。
           file [选项] 文件路径
           用法示例：
                file /dev/sda
                file /dev/pts/1

        rm 删除文件或目录(Remove)
           rm [选项] 文件或目录 ...
           rm 命令常用选项：
                -f      强制模式，永不提示，也不要求用户确认
                -i      交互模式，删除文件前请求用户确认
                -r      递归删除，即删除整个目录
                -v      输出当前操作的详细信息
           用法举例：
                rm -vi  file1        # 删除文件 file1
                rm -vir dir1        # 删除目录 dir1

        find 搜索文件
           find 命令非常强大，支持正规表达式(Regular Expression)，三言两语难尽述其妙，建议读者使用
                 中随时查阅其手册 man find。
           find 命令常用写法：
                find [选项] 路径 [其它选项]
           find 命令常用选项：
                -P              不跟随符号链接，即无视符号链接指向的文件
                -L              跟随符号链接
           find 命令常用的其它选项：
                -type <file_type>       查找指定的文件类型，可以是 f（普通文件），d（目录文件），
                                          c（字符设备文件），...
                -name <file_name>       查找特定文件，文件名大小写敏感
                -iname <file_name>      与 -name 相同，不过忽略大小写
                -maxdepth level         指定最多搜索的目录级别（目录层数），level 为具体的正数
                -mindepth level         指定至少要搜索的目录级别，level 为具体的正的数字
                -size [-/+] <file_size> 限定搜索文件的大小，file_size 为具体数字，单位可以
                                          是c w b k M G。数字前导的"-"或"+"号表示文件大小
                                          要“小于”或“大于”此数值，省略表示文件大小严格为此值。
                -regex pattern          使用正规表达式搜索文件，pattern 为文件名表达式
                -regextype type         限定 find 解析正规表达式的标准，type 可选值为 emacs（默认），
                                          posix-awk, posix-egrep, posix-extended
                -exec 命令 \;            执行命令。-exec 之后的内容都解析成命令的一部分，直至遇到分号 ";"，
                                          因为分号在 Bash Shell 中有特殊意义，故使用斜线 "\" 转义
           用法示例：
                find . -type f                         # 找出 "." 目录（即当前目录）中所有文件
                find ~ -name .bashrc                   # 在用户目录中查找名为 ".bashrc" 的文件
                find /usr -type f -iname "*StartOS*"   
                    # 在目录 /usr 中忽略大小写找出文件名中含有 "StartOS" 的文件, 注意：该命令中使用 
                    #    "*"号时使用了双引号，这是为了防止在 Shell 解析命令行参数阶段就展开 "*" 号，  
                    #   在 *inx 类系统众多的 Shell 中，星号 "*" 被解析成匹配所有。在 Shell 解析该
                    #   命令行的时候，就解析成当前目录所有的内容了，若不使用双引号， "*" 根本没传到
                    #   find 命令中。有兴趣的读者可以去掉双引号看看搜索结果有什么变化

                find /usr -size +2k -size -2M -regextype posix-egrep -regex ".*png$"    
                    # 在 /usr 目录中，找出大小在 2kB 到 2MB 之间，并且文件名以 png 结尾的文件。

                find ~ -type f -size +40M -exec file {} \;     
                    # 找出用户目录中 40MB 以上的文件，并使用 file 命令查探其类型。
                    # "{}" 代表 find 查找到的文件

        mkdir 创建目录(Make Directory)
           如果要创建的目录已经存在，则什么也不做
           mkdir [选项] 目录名1 ...
           mkdir 命令常用选项：
                -p|--parents    必要时，建立父目录
                -m              设置所建立目录的权限
                -v              输出当前操作详细的信息
           用法举例：
                mkdir -pv a/b/c   # 将按 a/b/c 层次结构建立 a b c 共 3 个目录, 因使用了 -p 选项，
                                  #   所以在 a 或 b 目录不存在时，会自动一起建立。如果不使用 -p，
                                  #   则父目录不存在时会报错
                mkdir a b c       # 在当前目录建立 a b c 三个目录

        rmdir 删除空目录(Remove Rirecotry)
           如果是非空目录，则报错，并不删除目录
           rmdir [选项]  空目录 ...
           rmdir 常用命令选项:
                -p|--parents    如果删除目录后，父目录也成为空目录，则一并删除之
                -v              输出当前操作详细的信息
           用法举例：
                rmdir -pv a/b/c  # 删除空目录 c，之后若 b 目录也为空，则删除 b 目录，...
                rmdir a b c      # 删除 a b c 三个空目录


        cat 输出文本文件内容(Concatenate)
           如果有多个文件，则依次输出到标准输出，相当于将数个文件的内容连接
           cat [选项] 文件1 ...
           cat 常用选项：
                -n      显示行号
           用法举例：
                cat /etc/yget.conf      # 输出文件 /etc/yget.conf 的内容到标准输出

        ls 列出目录内容(List)
           ls 命令使用频率非常高，这里只是列出最常用的几个选项，想要更大限度发挥 ls 功能，请查看其帮助
               页 ls --help
           ls [选项] 文件或目录 ...
           ls 命令常用选项:
                -l              长列表格式输出文件属性
                -R              递归列出，会遍历整个目录及其子目录
               --color=[WHEN]   根据输出文件的性质(文件或目录类型等),给项目着不同的颜色。 
                                   WHEN 的值可以是'always' (默认), 'never', 'auto', 
                                   意义分别为：总是，永不，自动
                -d              列出目录自身，而不是目录下的内容
                -h              人性化输出，如文件大小以 K,M,G 的方式标出
           用法示例：
                ls              列出当前目录的内容
                ls -Rl /tmp     列出 /tmp 目录及其子目录下所有文件的详细信息

        du 对文件/目录计算大小
           du [选项]  目录或文件 ...
           du 命令常用选项：
                -h              人性化输出，文件大小以 K,M,G 的方式标示
                -s              输出各个目录/文件的总的占用空间大小
           用法示例：
                du -h  ~        # 输出用户家目录下所有文件及子目录所占用的空间大小

        df 列出文件系统使用情况
           df [选项] [文件] ...
           df 命令常用选项：
                -a              所有文件系统
                -h              人性化输出信息
                -t <fs_type>      只输出 fs_type 限定的文件系统类型
                -T              输出文件系统类型
           用法示例：
                df -ht ext4     # 只输出类型为 ext4 的文件系统
                df -T
                df -h /dev/sda1 # 只输出第一块硬盘第一个分区的使用情况

        mount 挂载文件系统
           注：可能需要特权用户权限。另外 StartOS 的文件管理器默认自动挂载所有文件系统；因此练习时命令
              有可能报错。
           mount [选项] 设备 目标目录
           mount 命令常用选项：
                -t              指定文件系统类型，如 ntfs-3g, ext4 等
                -B              挂载目录
           用法示例：
                mount                             # 列出所有已经挂载的文件系统 
                mount -t ntfs-3g /dev/sda1 /mnt   # 挂载第一块硬盘第一个分区到 /mnt 目录下
                mount -B /media /mnt              # 这里将目录 /media 挂载到 /mnt 目录下，
                                                  #  这样无论 /mnt 或 /media 都可访问得到
                                                  #  /media 目录的内容，建站时或许非常有用

        umount 卸载文件系统
           注：需要特权用户权限。
           umount [选项] 设备或目录 ...
           umount 命令常用选项：
                -f              强制卸载目录
           用法示例：
                umount  /dev/sda1                 # 卸载已经挂载的文件系统 /dev/sda1 

        top 实时显示进程列表
           top 命令一旦运行，按字母“q”键退出。
           top [选项]
           top 命令常用选项：
                -p pidlist          只显示进程号位于为 pidlist 中的进程动态
                -d num              更新间隔时间。num 为时间，单位为秒(s)
           用法示例：
                top -d 1 -p 1,2     # 只监视进程号为 1,2 的两个进程，且每秒更新一次信息

        ps 列出当前系统运行的进程
           ps 命令接受3种形式的选项，虽然强大，但也使得用户面对选项搭配不知所措，有选项是冲突的，有选项
              功能是同一的，增加了使用难度。此处介绍只是 ps 的冰山一角，更详细的内容建 议查看其使用
              手册 man ps

           ps [选项]
           ps 命令常用选项：
                -e              显示所有进程
                -a              列出除会话首进程及未分配终端的进程外的所有进程
                -u userlist     以用户有效 ID 或用户名选择列出进程，ID 或名字位于 userlist 中
                -p pidlist      只列出指定进程号位于进程号列表 pidlist 的进程, 此选项可多次使用
               --ppid pidlist   只列出进程号位于 pidlist 中的进程的子进程
                 x              列出属于当前用户的进程
                -ax             列出所有进程。此处 'x' 与 'a' 联合使用，再组合其它选项时未必可用

           用法示例：
                ps -ax
                ps  x
                ps --ppid 1      # 列出父进程为 1 的进程

        pstree 列出当前系统所有进程，以树形方式体现其层次关系
           pstree [选项]
           pstree 命令常用选项：
                -a              命令参数一并列出
           用法示例：
                pstree

        pidof 根据进程名称查找进程号(pid)
           pidof [选项] 进程名称
           pidof 命令常用选项：
                -s              pidof 会尽可能多地输出某名称的进程号，该选项限定只需要输出一个
           用法示例：
                pidof lightdm

        kill 向进程发送信号
           kill [选项] pidlist
           kill 命令常用选项：
                -l              列出信号名
                -s signal       指定要发送的信号，默认是 15
           用法示例：
                kill -s 9 <PID>  # <PID> 为具体进程号（使用 pidof 命令查找），信号 9 是杀死进程

        killall 杀死进程
           killall [选项] 进程名称
           用法示例：
                killall firefox  # 杀死所有名为 "firefox" 的进程

        ping 往网络主机发送数据包
           用于网络联通测试。
           ping [选项] 主机
           ping 命令常用选项:
                -c      默认 ping 一直运行，直到用户按下 Ctrl-C 中止，该选项则限定 ping 的次数
           用法示例：
                ping localhost    # 测试本机 TCP/IP 协议是否正常，localhost 已被配置成代表本机

        ifconfig 查看/设置网络(Interface Configure)
           注：使用 ifconfig 设置网络时需要特权用户权限，并且设置不会被保存，所有改动重启后消失。
               Linux 系统中网络接口可理解成网卡，有线网卡编号为: eth0 eth1 ...；无线网卡编号为：
               wlan0 wlan1 ...
           ifconfig [选项]  [网络接口]
           ifconfig 网络接口 [协议地址簇] 选项 地址 ...   # 一般协议地址簇可省略，使用默认值
           ifconfig 命令常用选项：
                -a              显示所有网络接口
                up              开启网络接口
                down            关闭网络接口
                netmask         设置掩码
                broadcast       设置广播地址
           用法示例：
                ifconfig -a             # 显示所有网络接口信息
                ifconfig eth0 192.168.1.100 netmask 255.255.255.0 broadcast 192.168.1.255
                    # 以上命令设置有线网卡 IP 地址为 192.168.1.100, 子网掩码为 255.255.255.0, 
                    #    广播地址 192.168.1.255。如果子网掩码设置足以区别出广播地址，则广播地址一般可以
                    #    省略，由 ifconfig 自动配置
                ifconfig eth0 down
                ifconfig eht0 up        
                    # 练习中若配置出错造成无法上网，执行两行命令，分别关闭/开启一次，即可恢复原有设置

        netstat 查看网络状态(Network Status)
           netstat [选项]
           netstat 常用选项：
                -p      显示出进程信息
                -t      只列出与 tcp 协议有关的条目
                -u      只列出与 udp 协议有关的条目
                -n      端口，地址等使用数字而不是名称显示
                -a      显示所有
                -l      仅显示在监听状态的条目
           用法示例：
                netstat -atunp  # 显示出所有在使用 tcp 及 udp 协议的进程，及通信双方地址、端口号

 
解压缩
tar解压:tar xvf filename.tar打包:tar cvf filename.tar dirname 不压缩
.gz
解压1:gunzip filename.gz解压2:gzip -d filename.gz压缩:gzip filename
.tar.gz && .tgz
解压:tar zxvf filename.tar.gz压缩:tar zcvf filename.tar.gz dirname
.bz2
解压1:bzip2 -d filename.bz2解压2:bunzip2 filename.bz2压缩:bzip2 -z filename
.tar.bz2
解压1:tar jxvf filename.tar.bz2解压2:tar -bzip xvf filename.tar.bz2压缩:tar jcvf filename.tar.bz2 dirname
.bz
解压1:bzip2 -d filename.bz解压2:bunzip2 filename.bz压缩:?.Tar.bz
解压：Tar jxvf FileName.Tar.bz
压缩：未知
.Z
解压：uncompress FileName.Z
压缩：compress FileName
.Tar.Z
解压：Tar Zxvf FileName.Tar.Z
压缩：Tar Zcvf FileName.Tar.Z DirName
.zip
解压：unzip FileName.zip
压缩：zip FileName.zip DirName
.rar
解压：rar x FileName.rar
压缩：rar a FileName.rar DirName
.lha
解压：lha -e FileName.lha
压缩：lha -a FileName.lha FileName
.rpm
解包：rpm2cpio FileName.rpm | cpio -div
.deb
解包：ar p FileName.deb data.Tar.gz | Tar zxf -
.Tar .tgz .Tar.gz .Tar.Z .Tar.bz .Tar.bz2 .zip .cpio .rpm
.deb .slp .arj .rar .ace .lha .lzh .lzx .lzs .arc .sda .sfx .lnx
.zoo .cab .kar .cpt .pit .sit .sea
解压：sEx x FileName.*
压缩：sEx a FileName.* FileName



pip代理设置方法
sudo pip install --proxy=172.16.155.154:3128 django-tastypie
在用户目录下面有.pip隐藏目录.
复制隐藏文件

把dira目录中的隐藏文件复制到dirb中:

正解一：
cp -a /tmp/dira/. /tmp/dirb
man 一下 cp
-a ,--archive
same as -dpR

正解二：
cp /tmp/dira/.[^.]* /tmp/dirb

误区一：
cp -rf /tmp/dira/* /tmp/dirb
* 不包括隐藏文件。

误区二：
cp -rf /tmp/dira/.* /tmp/dirb
.* 包括了所有的文件和目录，但是也把 . 和.. 这两个包括在内，所以会递归复制，父目录的所有文件。

误区三：
cp -rf `ls -A /tmp/dira | grep '^.[^.]*'` /tmp/dirb
也会出现隐藏文件的一些错误。






设置Bash颜色
\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\W\[\033[00m\]\$
记录正在进行的工作
～/.bashrc
shopt -s histappend#修复用户打开多终端，信息可能丢失的问题。
PROMPT_COMMAND='history -n;history -a'
HISTSIZE=10000#增加条数
HISTFILESIZE=10000
添加调试
比如perl：
my $debug=1;#set to 0 to turn off debug output
print "At step 1\n" if $debug
集中管理網絡資源：Kerberos LDAP 和 NFS
sudo apt-get install krb5-kdc krb5-admin-server libkrb5-dev krb5-config krb5-user krb5-clients libkadm5clnt-mit8



Linux Proxy设置
.bashrc里面加入:
export all_proxy=socks://172.16.155.150:3128/
export http_proxy=http://172.16.155.150:3128/
export https_proxy=https://172.16.155.150:3128/
export ftp_proxy=ftp://172.16.155.150:3128/
export socks_proxy=socks://172.16.155.150:3128/

或者是去 创建一个 /etc/apt/apt.conf 然后在里面加入

Acquire::http::proxy "http://proxy.pal.sap.corp:8080/";
Acquire::ftp::proxy "ftp://proxy.pal.sap.corp:8080/";
Acquire::https::proxy "https://proxy.pal.sap.corp:8080/";

查看硬件信息
sudo lshw

nslookup www.baidu.com  #跟踪域名解析过程
dig www.baidu.com 


SSH
在~/.ssh里面
vi config

Host ec2-dm1
HostName 54.169.114.90
User ubuntu
IdentityFile ~/.ssh/microsite1.pem
CompressionLevel 6
DynamicForward localhost:3128


装机必设
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"
PS1="\[\033[0;33m\][\!]\`if [[ \$? = "0" ]]; then echo "\\[\\033[32m\\]"; else echo "\\[\\033[31m\\]"; fi\`[\u.\h: \`if [[ `pwd|wc -c|tr -d " "` > 18 ]]; then echo "\\W"; else echo "\\w"; fi\`]\$\[\033[0m\] "; echo -ne "\033]0;`hostname -s`:`pwd`\007"
export http_proxy=http://proxy.pal.sap.corp:8080/
export https_proxy=http://proxy.pal.sap.corp:8080/

declare -x ALL_PROXY="socks://proxy.pal.sap.corp:8080/"
declare -x NO_PROXY="localhost,127.0.0.0/8,::1"
declare -x UBUNTU_MENUPROXY="1"
declare -x all_proxy="socks://proxy.pal.sap.corp:8080/"
declare -x ftp_proxy="ftp://proxy.pal.sap.corp:8080/"
declare -x http_proxy="http://proxy.pal.sap.corp:8080/"
declare -x https_proxy="https://proxy.pal.sap.corp:8080"
declare -x no_proxy="localhost,127.0.0.0/8,::1"
declare -x socks_proxy="socks://proxy.pal.sap.corp:8080/"

RPM

rpm -qa|gre ctags  #查看是否安装ctags.


zypper 命令
    zypper se automake 搜索包
    zypper in automake 安装包
    zypper if automake 查看包信息

CentOS yum的详细使用方法
yum = Yellow dog Updater, Modified 
主要功能是更方便的添加/删除/更新RPM包. 
它能自动解决包的倚赖性问题. 
它能便于管理大量系统的更新问题
yum特点
可以同时配置多个资源库(Repository) 简洁的配置文件(/etc/yum.conf 自动解决增加或删除rpm包时遇到的倚赖性问题 使用方便 保持与RPM数据库的一致性
yum安装
CentOS自带(yum-*.noarch.rpm)
#rpm -ivh yum-*.noarch.rpm
在第一次启用yum之前首先需要导入系统的RPM-GPG-KEY：
#rpm --import /usr/share/doc/centos-release-3(4)/RPM-GPG-KEY-CentOS-3(4)
yum指令
注:当第一次使用yum或yum资源库有更新时,yum会自动下载所有所需的headers放置于/var/cache/yum目录下,所需时间可能较长.
rpm包的更新
检查可更新的rpm包
#yum check-update
更新所有的rpm包
#yum update
更新指定的rpm包,如更新kernel和kernel source
#yum update kernel kernel-source
大规模的版本升级,与yum update不同的是,连旧的淘汰的包也升级
#yum upgrade
rpm包的安装和删除
安装rpm包,如xmms-mp3
#yum install xmms-mp3
删除rpm包,包括与该包有倚赖性的包
#yum remove licq
注:同时会提示删除licq-gnome,licq-qt,licq-text
yum暂存(/var/cache/yum/)的相关参数
清除暂存中rpm包文件
#yum clean packages
清除暂存中rpm头文件
#yum clearn headers
清除暂存中旧的rpm头文件
#yum clean oldheaders
清除暂存中旧的rpm头文件和包文件
#yum clearn 或#yum clearn all
注:相当于yum clean packages + yum clean oldheaders
包列表
列出资源库中所有可以安装或更新的rpm包
#yum list
列出资源库中特定的可以安装或更新以及已经安装的rpm包
#yum list mozilla#yum list mozilla*
注:可以在rpm包名中使用匹配符,如列出所有以mozilla开头的rpm包
列出资源库中所有可以更新的rpm包
#yum list updates
列出已经安装的所有的rpm包
#yum list installed
列出已经安装的但是不包含在资源库中的rpm包
#yum list extras
注:通过其它网站下载安装的rpm包
rpm包信息显示(info参数同list)
列出资源库中所有可以安装或更新的rpm包的信息
#yum info
列出资源库中特定的可以安装或更新以及已经安装的rpm包的信息
#yum info mozilla#yum info mozilla*
注:可以在rpm包名中使用匹配符,如列出所有以mozilla开头的rpm包的信息
列出资源库中所有可以更新的rpm包的信息
#yum info updates
列出已经安装的所有的rpm包的信息
#yum info installed
列出已经安装的但是不包含在资源库中的rpm包的信息
#yum info extras
注:通过其它网站下载安装的rpm包的信息
搜索rpm包
搜索匹配特定字符的rpm包
#yum search mozilla
注:在rpm包名,包描述等中搜索
搜索有包含特定文件名的rpm包
#yum provides realplay
增加资源库
例如:增加rpm.livna.org作为资源库
安装Livna.org rpms GPG key
#rpm --import http://rpm.livna.org/RPM-LIVNA-GPG-KEY
检查GPG Key
# rpm -qa gpg-pubkey*
显示Key信息
#rpm -qi gpg-pubkey-a109b1ec-3f6e28d5
(注:如果要删除Key,使用#rpm -e gpg-pubkey-a109b1ec-3f6e28d5)
yum常用的命令
# yum install xxx            安装xxx软件
# yum info xxx                查看xxx软件的信息
# yum remove xxx        删除软件包
# yum list                        列出软件包
# yum clean                    清除缓冲和就的包
# yum provides xxx        以xxx为关键字搜索包（提供的信息为关键字）
# yum search xxx           搜索软件包（以名字为关键字）
# yum groupupdate xxx
# yum grouplist xxx
# yum groupremove xxx
这三个都是一组为单位进行升级 列表和删除的操作。。比如 "Mysql Database"就是一个组会同时操作相关的所有软件包；
# yum update                系统升级
# yum list available        列出所有升级源上的包
# yum list updates         列出所有升级源上的可以更新包；
# yum list installed         列出已经安装的包；
# yun update kernel       升级内核；

yum常用的源
1) 自动选择最快的源
由于yum中有的mirror速度是非常慢的，如果yum选择了这个mirror，这个时候yum就会非常慢，对此，可以下载fastestmirror插件，它会自动选择最快的mirror：
#yum install yum-fastestmirror
配置文件：（一般不用动）/etc/yum/pluginconf.d/fastestmirror.conf
你的yum镜像的速度测试记录文件：/var/cache/yum/timedhosts.txt
(2)使用图形界面的yum
如果觉得命令行的yum不方便，那么可以使用图形化的yumex，这个看起来更方便，因为可以自由地选择软件仓库：
#yum install yumex
然后在系统工具中就可以看到yum extender了。实际上系统自带的“添加/删除程序“也可以实现图形化的软件安装，但有些yumex的功能它没有。


