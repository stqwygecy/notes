<link rel="stylesheet" type="text/css" href="./github.css">
# Linux常用命令

[更详细命令参考1](https://www.cnblogs.com/wei-91/p/6592627.html)

[更详细命令参考2](https://www.cnblogs.com/maybe2030/p/4562282.html)

### 1. pwd指令(显示当前工作目录)

```bash
pwd		显示当前所在的工作目录
```

### 2. ls指令

```bash
ls [选项] [linux路径]	 #查看文件信息
ls						以平铺形式，列出当前工作目录下的内容
ls -a 					列出全部文件（包含隐藏的文件/文件夹）
ls -l					以列表（竖向排列）的形式展示内容，并展示更多信息
ls -h					需要和【-l】选项搭配使用，以更加人性化的方式显示文件的大小单位
ll           			以列表的方式显示
```

**提示：**以【.】开头的，表示是Linux系统的隐藏文件/文件夹（只要以【.】开头，就能自动隐藏），**命令的选项是可以组合使用的，比如：【ls -lah】，等同于【ls -a -l -h】**

### 3. cd指令

```bash
cd [linux路径]
cd		回到家目录
cd ~	回到家目录
cd ..   回到上一级目录
```

**特殊路径符：**

1. 【.】当前目录
2. 【..】上级目录
3. 【~】家目录

### 4. mkdir指令(创建文件夹)

```bash
mkdir [选项] 路径		创建文件夹
mkdir -p 路径			 创建多层级目录，自动创建不存在的父目录，适用于创建【连续多层级的目录】
```

### 5. rmdir指令(删除文件夹)

```bash
rmdir [选项] 路径			删除空文件夹
rmdir -p 路径/			 递归删除空文件夹
rmdir -R 路径			 	 递归删除空文件夹
【文件夹下有内容,则无法删除】
```

### 6. touch 指令(创建文件)

```bash
touch 文件路径
【可以一次创建多个文件】
touch 文件路径1 文件路径2
```

### 7. cp指令(复制文件或文件夹)

```bash
【拷贝文件到目标路径】
cp [选项] 源路径 目标路径
cp 源路径 目标路径  			拷贝单个文件
cp -r 源路径 目标路径			拷贝文件夹
```

**注意：**当拷贝时发现相同文件,会提示[是否覆盖?]**【\cp [选项] 源路径 目标路径】**		取消提示,强制复制

### 8.  rm指令(删除文件或文件夹)

```bash
【删除目录或者文件】
rm [选项] 目标路径1 目标路径2 ... 目标路径n
rm 文件路径			  	  删除【文件】
rm -r 文件夹路径			 删除【文件夹】
rm -f xxxx				强制删除不提示
```

**注意：**rm命令支持通配符【*】，用来做模糊匹配

### 9. mv指令(移动文件或文件夹)

```bash
【移动文件或重命名】
mv 源路径 目标路径			目标路径如果目标不存在，则进行改名，确保目标存在
```

### 10. cat指令(查看文件内容)

```bash
【显示文件内容】
cat [选项] 文件路径
cat 文件路径		显示文件内容
cat -n 文件路径		显示文件内容,并显示行号
```

**补充说明：**

正常情况为了方便阅读,我们会在cat指令最后加上管道符"|",把内容传给more,分页显示如:

```bash
cat -n /etc/profile | more
```

### 11. more指令(翻页查看文件内容)

```bash
【more指令是基于vi编辑器的文本过滤器,以全屏的方式按页显示文本内容】（more指令中内置了很多快捷键,用起来很方便）
more 文件路径
【快捷键】
空格			向下翻一页
Enter		 向下翻一行
q			 立即离开
Ctrl+F		 向下滚动一屏
Ctrl+B		 向上滚动一屏
=			 显示当前行号
:f			 输出文件名和当前行号
```

### 12. less指令

```bash
【比more更加强大,功能比more更过,这里只介绍部分】
less 文件路径
【快捷键】
空格				 向下翻一页
pagedown		  向下翻一页
pageup			  向上翻一页
/字符串		    向下查找[字符串],n下一个,N上一个
?字符串			向上查找[字符串],n下一个,N上一个
q				  离开less
```

### 13. >指令与>>指令(重定向符)

```bash
【把前方语句的结果存进文件,若文件不存在会自动创建】
> 输出重定向			会覆盖原来文件内容
>> 追加重定向		追加到文件末尾
```

**其他重定向符：**

```bash
2>		#将标准错误输出重定向到文件，覆盖原有文件内容。
2>>		#将标准错误输出重定向到文件，追加到原有文件内容之后。
&>>		#将标准输出和标准错误输出都重定向到文件，追加到原有文件内容之后。
```

### 14. echo指令和反引号 `

```bash
【把内容输出到控制台,复杂内容可以用【""】包围】
如下:
echo "我是杨家三少"
echo $PATH
```

```bash
用反引号（通常也称之为飘号）将其包围被包围的内容，会被作为命令执行，而非普通字符
比如：
echo `pwd`
```

### 15. head指令

```bash
【head用于显示文件的开头部分内容，默认情况下
head 指令显示文件的前10 行内容】
head 文件路径			查看文件前10行
head -n 5 文件路径		查看文件前5行
```

### 16. tail指令(查看文件结尾内容与跟踪文件的最新更改)

```bash
【tail用于显示文件的结尾部分内容，默认情况下tail指令显示文件的后10行内容，【还可以跟踪文件的最新更改】】
tail [-f -num] linux路径		 num表示一个数字
tail 文件路径					查看文件前10行
tail -n 5 文件路径				查看文件前5行
tail -f 文件路径				实时追踪文件所有的更新-----经常使用
```

### 17. ln指令(创建软链接)

```bash
【软链接也叫符号链接，类似于 windows 里的快捷方式，主要存放了链接其他【文件或文件夹】的路径】
ln -s 源文件或源文件夹 软连接名(要链接去的目的地)		#【软连接名】就是【路径】
```

<mark>注意：这里必须用绝对路径</mark>

### 18. history指令

```bash
【查看已经执行过历史命令,也可以执行历史指令】
history 		查看所有的历史指令
history 10		查看最近执行的10条指令
!100			执行编号为100的指令
```

### 19. date 指令

```bash
date [-d] [计算的时间差（配合 -d 使用）] [+格式化字符串]			#第二个参数如果要带，【+】号就必须带上
date 			显示当前日期
data +%Y		显示当前年份
data +%m		显示当前月份
data +%d		显示当前天
data "+%Y-%m-%d %H:%M:%S"		#常用

#【-d】按照给定的字符串显示日期，一般用于【日期计算】
#【-d】支持的时间标记有以下：(在时间标记前需使用【正负号】和一个【空格】表示计算)，比如 【date "+1 day"】
year	年
Month	月
day		天
hour	小时
minute	分钟
second	秒
#格式化字符串：通过特定的字符串标记，来控制显示的日期格式
#详细的格式化字符串
%Y		年
%y		年份后两位数字
%m		月份
%d		日
%H		小时
%M		分钟
%S		秒
%s		自1970-01-01 00:00:00 UTC到现在的秒数(时间戳)
```

**提示：**通过date查看的日期时间是不准确的，这是因为：系统默认时区非【中国的东八区】。

**修改时区：**(建议root账号，也可以使用【ntp服务】自动校准)	[ntp校准](#36.-yum命令(安装软件))

1. `rm -f /etc/localtime`:	将系统自带的localtime文件删除
2. `sudo ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime`:    将/usr/share/zoneinfo/Asia/Shanghai文件链接为localtime文件

### 20. cal指令

```bash
【查看日历】
cal 		显示当前日历
cal 2020 	显示2020年的日历
```

### 21. find指令(查找文件或文件夹)和which指令(查看命令的程序文件)

```bash
【find指令将从指定目录向下递归地遍历其各个子目录，将满足条件的文件或者目录显示在终端】
find [范围] [选项] "被查找文件名"
find 起始路径 -name "被查找文件名"		被查找文件名，支持使用通配符【*】来做模糊查询
【范围:指路径,不写默认从当前向下找,类似于windows的查找】

选项:
-name 文件名		按文件名查找
-user 用户名		查找属于该用户的所有文件
-size 			  按文件大小查找
	+20M		  大于20M的文件或文件夹
	-20M		  小于20M的文件或文件夹
	20M
	20k			  k是小写字母，大小单位有【k,M,G】
```

```bash
which指令查看所使用的一系列命令的程序文件存放在哪里
which 指令名		查看命令的程序文件存放位置
```

### 22. grep 指令 和 管道符号 |

```bash
【grep:过滤查找，从文件中通过关键字过滤文件行】
grep [选项] 关键字 文件路径			关键字带有空格或其它特殊符号，建议使用【""】将关键字包围起来，文件路径这项参数可作为【内容输入端口】

选项:
-n		显示匹配行及行号
-i		忽略字母大小写
```

**注意：过滤内容支持正则**

```bash
【管道符:"|",表示将前一个命令的处理结果输出传递给后面的命令处理】(将管道符左边命令的结果，作为右边命令的输入)
```

### 23. wc命令(做数量统计)

```bash
【可以通过wc命令统计文件的行数、单词数量等】
wc [-c -m -l -w] 文件路径
-c		统计bytes数量
-m		统计字符数量
-l		统计行数
-w		统计单词数量
```

### 24. gzip/gunzip 指令

```bash
【用于压缩和解压文件】
gzip 文件路径
gunzip gz文件路径
【说明:使用gzip压缩文件之后,不会保留原来的文件】

例子:
1.将 /home 下的 1.txt 文件使用gzip压缩
2.将 /home 下的 1.txt.gz 文件使用gunzip解压
```

### 25. zip/unzip 指令

```bash
【zip 用于压缩文件， unzip 用于解压的，这个在项目打包发布中很有用的】
zip [选项] xxx.zip 被压缩内容			压缩文件或者目录
	-r 								压缩目录

unzip [选项] xxx.zip  			    解压文件	
	-d 目录							指定压缩后的存放目录
```

**例子:**

1. 将 /home 下的 所有文件进行压缩成 mypackage.zip
2. 将mypackge.zip解压到/opt/tmp下

### 26. tar指令

```bash
【tar 指令 是打包指令，最后打包后的文件是【.tar.gz】的文件】

压缩:
tar -zcvf xx.tar.gz  被压缩内容			 		   压缩
tar -zxvf xx.tar.gz	 -C 目标路径					解压

例子:
1.压缩多个文件，将  /home/a1.txt 和  /home/a2.txt 压缩成	a.tar.gz
2.将/home 的文件夹 压缩成 myhome.tar.gz
3.将  a.tar.gz	解压到当前目录
4.将 myhome.tar.gz	解压到 /opt/ 目录下
```

### 27. man 指令与help指令

```bash
man  	指令名
help 	指令名
```

### 28. vi/vim编辑器

**提示：**

1. 如果文件路径表示的文件【不存在】，那么此命令会用于编辑【新文件】

2. 如果文件路径表示的文件【存在】，那么此命令用于编辑【已有文件】

**命令模式下**

```bash
dd			删除行
ndd			删除光标向下 n 行
yy			复制当前行
nyy			复制当前行和下面的 n 行
p			粘贴复制的内容
u			撤销文本编辑
ctrl + r	方向撤销修改
gg			跳到行首
G			跳到行尾
/			进入搜索模式
n			向下继续搜索
N			向上继续搜索
```

![image-20230315221050039.png](https://s2.loli.net/2023/05/06/2Lbdvo43ARKFMsp.png)

**底线命令模式下**

```bash
:wq			保存并退出
:q			仅退出
:q!			强制退出
:w			仅保存
:set nu		显示行号
:set paste	设置粘贴模式
```

![image-20230315222205678.png](https://s2.loli.net/2023/05/06/Y8h2Li6N7OV4TkH.png)

### 29. su指令和exit指令

```bash
su [-] [用户名]
【-】符号是可选的，表示是否在切换用户后【加载环境变量】（后续讲解），建议带上
参数：用户名，表示要切换的用户，用户名也可以省略，省略表示切换到root,切换用户后，可以通过【exit】命令退回上一个用户，也可以使用快捷键：【ctrl+d】
```

### 30. sudo指令

```bash
使用【sudo】，我们需要为普通用户配置【sudo认证】
sudo 其他命令
```

**sudo认证：**

1. 切换到root用户，**执行【`visudo`】命令**，会自动通过vi编辑器打开：【/etc/sudoers】
2. 在文件的最后添加【`用户名 ALL=(ALL)    NOPASSWD:ALL`】，其中最后的NOPASSWD:ALL表示使用sudo命令，无需输入密码

### 31. groupadd与groupdel

<mark>以下命令需root用户执行</mark>

```bash
groupadd 用户组名 		#创建用户组
groupdel 用户组名		#删除用户组
```

### 32. useradd、userdel、id、usermod

```bash
useradd [-g -d] 用户名	[用户组 用户家目录路径]	#创建用户
·选项：-g指定用户的组，【不指定-g，会创建同名组并自动加入】，指定-g需要组已经存在，如【已存在同名组，必须使用-g】
·选项：-d指定用户【HOME路径】，不指定，HOME目录默认在：【/home/用户名】
useradd test2 -g itcast -d /home/test222	#【test2 是用户名】，【itcast是所属用户组】，【/home/test222是用户家目录】

userdel [-r] 用户名		#删除用户
·选项：-r，删除用户的HOME目录，【不使用-r，删除用户时，【HOME目录保留】】

id [用户名]				#查看用户所属组
·参数：用户名，被查看的用户，如果【不提供则查看自身】

usermod -aG 用户组 用户名	  #修改用户所属组，将指定用户加入指定用户组
```

### 33. getent指令

```bash
getent passwd		#查看当前系统中有哪些用户
getent group		#查看当前系统中有哪些用户组
```

提示：【getent passwd】与【`cat /etc/passwd`】效果是一致的，查询结果七对信息分别对应【【用户名】：【密码】（x）：【用户ID】：【组ID】：【描述信息】（无用）：【HOME目录】：【执行终端】（默认bash）】,<mark>getent group</mark>返回结果包含3份信息，【组名称】：【组认证】（显示为x）：【组ID】

### 34. chmod指令(权限修改)

```bash
chmod [-R] 权限 文件或文件夹		#【-R】，对文件夹内的全部内容应用同样的操作
#权限可以用3位数字来代表，第一位数字表示用户权限，第二位表示用户组权限，第三位表示其它用户权限。
#数字的细节如下：【r记为4】，【w记为2】，【x记为1】

#示例：
chmod u=rwx,g=rx,o=x hello.txt		 #将文件权限修改为：【rwxr-x--x】,其中：【u】表示user所属用户权限，【g】表示group组权限，【o】表示other其它用户权限
chmod -R u=rwx,g=rx,o=x test		#将【文件夹test以及文件夹内全部内容】权限设置为：【rwxr-x--x】
```

**注意: **

1. 只有文件、文件夹的所属用户或root用户可以修改

2. 针对文件、文件夹的不同，rwx的含义有细微差别
   **-r**，针对**文件**可以查看文件内容
   ·针对**文件夹**，可以查看文件夹内容，如【ls】命令
   **-w**，针对**文件**表示可以修改此文件
   ·针对**文件夹**，可以在文件夹内：【创建、删除、改名】等操作
   **-x**，针对**文件**表示可以将文件作为程序执行
   ·针对**文件夹**，表示可以【更改工作目录到此文件夹】，即【cd】进入

**提示：** 

![image-20230316112531703.png](https://s2.loli.net/2023/05/06/lvjfLBEOPG9Nrpg.png)

**序号1对应字母含义：**

![image-20230316112717158.png](https://s2.loli.net/2023/05/06/He2z6DfRXCjPl8w.png)

### 35. chown指令(修改文件、文件夹的所属用户和用户组)

```bash
#使用chown命令，可以修改文件、文件夹的所属用户和用户组普通用户无法修改所属为其它用户或组，所以此命令【只适用于root用户】执行
chown [-R] [用户][:][用户组] 文件或文件夹
·选项，-R，同chmod，对文件夹内全部内容应用相同规则
·【:】用于分隔用户和用户组

#示例
chown root hello.txt			#将hello.txt所属用户修改为root 
chown :root hello.txt			#将hello.txt所属用户组修改为root 
chown root:itheima hello.txt	#将hello.txt所属用户修改为root，用户组修改为itheima 
chown -R root test				#将文件夹test的所属用户修改为root并对文件夹内全部内容应用同样规则
```

### 36. yum命令(安装软件)

```bash
#yum:RPM包软件管理器，用于自动化安装配置Linux软件，并可以自动解决依赖问题。
yum [-y] [install | remove | search] 软件名称
·选项：【-y】，自动确认，无需手动确认安装或卸载过程
·install：	#安装
·remove：	#卸载
·search：	#搜索
#yum命令需要root权限哦，可以【su切换到root】，或使用【sudo提权】。
#yum命令需要联网
```

**可能需要用到的指令：**

1.  `yum -y install wget`		[跳转至wget命令使用](#39. wget命令(下载网络文件))

​		wget是Linux操作系统下的一个【命令行下载工具】，它可以从网站上下载文件或整个网站。wget支持HTTP、HTTPS和FTP等多种协议，可以在后台运行，支		持断点续传、限速、递归下载等功能。

2. `yum install -y ntp`

   安装【ntp软件】可以通过ntpd服务名，配合systemctl进行控制，ntp是Linux操作系统下的一个网络时间协议（Network Time Protocol）客户端程序，用于【同步本地计算机的时间与网络时间服务器上的标准时间】。

   <mark>ntp服务使用:</mark>

   ```bash
   启动并设置开机自启：
   systemctl start ntpd
   systemctl enable ntpd		#当ntpd启动后会定期的帮助我们联网校准系统的时间
   #也可以手动校准（需root权限）,如下
   ntpdate -u ntp.aliyun.com	#通过阿里云提供的服务网址配合ntpdate（安装ntp后会附带这个命令）命令自动校准
   ```

3. `yum install -y httpd`

   安装【apache服务器软件】可以通过httpd服务名，配合systemctl进行控制，httpd是Linux操作系统下的一个Web服务器程序，全称为Apache HTTP Server。【它是一个开源的、跨平台的Web服务器】

4. `yum -y install nmap`    [跳转至nmap指令使用](#41. nmap命令(查看端口占用))
5. `yum -y install net-tools`    [跳转至netstat指令使用](#42. netstat命令(查看指定端口占用))
6. `yum -y install lrzsz`     [跳转至rz,sz指令使用](#48. rz,sz命令(上传与下载))

<mark>注意：部分软件安装后没有自动集成到systemctl中，我们可以手动添加。</mark>

### 37. systemctl命令(启动、停止、开机自启服务)

```bash
systemct1 start | stop | status | enable | disable 服务名		#启动、停止、开机自启服务
#start		启动
#stop		关闭
#status 	查看状态
#enable 	开启开机自启
#disable	关闭开机自启
```

说明：

1. NetworkManager，主网络服务
2. network，副网络服务
3. firewalld，防火墙服务
4. sshd，ssh服务（FinalShell远程登录Linux使用的就是这个服务）

### 38. ping命令(检查网络是否是可联通状态)

```bash
ping [-c num] ip或主机名
·选项：-c，检查的次数，不使用-c选项，将无限次数持续检查
·参数：ip或主机名，被检查的服务器的ip地址或主机名地址
```

### 39. wget命令(下载网络文件)

```bash
语法：wget[-b]ur1
·选项：-b，可选，后台下载，会将日志写入到当前工作目录的wget-log文件
·参数：url，下载链接
```

### 40. curl命令(发送http网络请求)

```bash
curl可以发送http网络请求，可用于：下载文件、获取信息等
cur1 [-O] ur1
·选项：-O，用于下载文件，当url是下载链接时，可以使用此选项保存文件
·参数：url，要发起请求的网络地址
```

**提示：**查看公网IP地址 `curl cip.cc`

### 41. nmap命令(查看端口占用)

```bash
nmap 被查看的IP地址
```

### 42. netstat命令(查看指定端口占用)

```bash
netstat -anp | grep 端口号
```

### 43. ps命令(查看进程信息)

```bash
ps [-e -f]		#一般来说，【固定用法】就是：【ps -ef】列出全部进程的全部信息
选项：-e，显示出全部的进程
选项：-f，以完全格式化的形式展示信息（展示全部信息）
```

### 44. kill命令(关闭进程)

```bash
kill [-9] 进程ID
选项：-9，表示【强制】关闭进程。不使用此选项会向进程发送信号【要求其关闭】，但是否关闭看进程自身的处理机制。
```

### 45. top命令(查看系统资源占用)

```bash
top		#按【q】或【ctrl+c】退出，查看CPU、内存使用情况，类似Windows的任务管理器【默认每5秒】刷新一次
-p		#只显示某个进程的信息
-d		#设置刷新时间，默认是5s
-c		#显示产生进程的完整命令，默认是进程名
-n		#指定刷新次数，比如top -n 3，刷新输出3次后退出
-b		#以非交互非全屏模式运行，以批次的方式执行top，一般配合-n指定输出几次统计信息，将输出重定向到指定文件，比如top -b -n 3 > /tmp/top.tmp
-i		#不显示任何闲置（idle）或无用（zombie）的进程
-u		#查找特定用户启动的进程
```

<mark>**top命令结果详解：**</mark>

![image-20230316204432348.png](https://s2.loli.net/2023/05/06/duU3VZPSv28LsMx.png)

![image-20230316205131700.png](https://s2.loli.net/2023/05/06/uQYmNOS6IP27MCJ.png)

<mark>**top指令交互模式下的指令：**</mark>

![image-20230316210343420.png](https://s2.loli.net/2023/05/06/xD7hRmjVHXo96GN.png)

### 46. df(磁盘信息监控)

```bash	
df [-h]		#查看硬盘的使用情况
选项：-h，以更加人性化的单位显示
```

### 47.iostat(查看CPU、磁盘相关信息)

```bash
iostat [-x] [num1] [num2]		#查看CPU、磁盘的相关信息
·选项：-x，显示更多信息
·num1：数字，刷新间隔
·num2：数字，刷新几次
```

**-x参数的结果详解：**

![image-20230316211321291.png](https://s2.loli.net/2023/05/06/lPHFVqtaenjomIW.png)

### 48. rz,sz命令(上传与下载)

```bash
rz		#上传(速度较慢)
sz		#要下载的文件
```

### 49. tar命令与zip、unzip命令(压缩与解压)

```bash
tar [-c -v -x -f -z -C] 参数1 参数2 ... 参数N
·-c，创建压缩文件，用于【压缩模式】
·-v，显示压缩、解压过程，用于【查看进度】
·-x，【解压模式】
·-f，要创建的文件，或要解压的文件，【-f选项必须在所有选项中位置处于【最后一个】】
·-z，【gzip模式】，不使用-z就是普通的【tarball格式】
·-C，选择【解压的目的地】，用于【解压模式】

# tar压缩的常用组合为：
tar -cvf test.tar 1.txt 2.txt 3.txt 		#将1.txt 2.txt 3.txt 压缩到test.tar文件内
tar -zcvf test.tar.gz 1.txt 2.txt 3.txt		#将1.txt 2.txt 3.txt 压缩到test.tar.gz文件内，使用gzip模式

# 常用的tar解压组合有
tar -xvf test.tar		#解压test.tar，将文件解压至当前目录
tar -xvf test.tar -C /home/itheima		#解压test.tar，将文件解压至指定目录（/home/itheima）
tar -zxvf test.tar.gz -C /home/itheima	#以Gzip模式解压test.tar.gz，将文件解压至指定目录（/home/itheima）
```

提示：

1. 【.tar】，称之为tarball，归档文件，即简单的将文件组装到一个.tar的文件内，并没有太多文件体积的减少，仅仅是简单的封装
2. 【.gz】，也常见为.tar.gz，gzip格式压缩文件，即使用gzip压缩算法将文件压缩到一个文件内，可以极大的减少压缩后的体积
3. 【-z】选项如果使用的话，一般处于选项位第一个
4. 【-f】选项，【必须】在选项位最后一个
5. 【-C】选项单独使用，和解压所需的其它参数分开

```bash
zip [-r] 参数1 参数2 ... 参数N		#参数【-r】，被压缩的包含文件夹的时候，需要使用-r选项，和rm、cp等命令的-r效果一致
zip test.zip a.txt b.txt c.txt		#将a.txt b.txt c.txt压缩到test.zip文件内
zip -r test.zip test itheima a.txt	#将test、itheima两个文件夹和a.txt文件，压缩到test.zip文件内
```

```bash
unzip [-d] 参数...
#-d，指定要解压去的位置，同tar的-C选项
#参数，被解压的zip压缩包文件
示例：
unzip test.zip						#将test.zip解压到当前目录
unzip test.zip -d /home/itheima		#将test.zip解压到指定文件夹内（/home/itheima）
```

### 50. rpm命令(安装、升级、删除和查询软件包)

```bash
#RPM（Red Hat Package Manager）是一种软件包管理器，用于安装、升级、删除和查询软件包
-i：安装软件包
-v：显示详细安装/升级过程
-h：显示安装/升级进度条
-U：升级软件包
-e：删除软件包
-qa：查询已安装的所有软件包
-qi：查询软件包详细信息
-ql：查询软件包文件列表
-qR：查询软件包依赖关系
-qf：查询软件包提供的文件
--whatprovides：查询软件包所属的仓库
--import: 用于导入公钥或证书
#其中，-i、-U 和 -e 是互斥的，只能同时使用其中一个参数。
```



# VM安装

**注意：**VMware安装好后，确保下图两个东西存在。快速查看方式：桌面`windows + r` 输入【`ncpa.cpl`】,回车。

![image-20230315150704643.png](https://s2.loli.net/2023/05/06/dpYvGgyJxZhq9tC.png)



# CentOS安装

[阿里云镜像网站下载CentOS](https://mirrors.aliyun.com/centos/?spm=a2c6h.13651104.0.0.5018320cBmcdnT)

[安装CentOS详细过程](https://www.bilibili.com/opus/751006896271392807?spm_id_from=333.999.0.0)



# FinalShell远程连接到Linux操作系统

[windows下载FinalShell](http://www.hostbuf.com/downloads/finalshell_install.exe)

[FinalShell官方网站](https://hostbuf.com)

**软件安装后提示：**

```bash
终端使用帮助

相关快捷键

终端:
alt 命令历史
双击ctrl 切换到命令输入框

命令输入框:
alt 命令历史
tab 补全 
双击ctrl 切换到终端

列表窗口:
backspace 上一级目录
alt/tab/esc 关闭窗口
上下箭头 选择行
```



# Linux根目录下各种文件夹的作用

1. /bin：该文件夹存放的是系统启动和运行时需要使用的基本命令和工具。这些命令和工具可以被所有用户使用。
2. /sbin：该文件夹存放的是系统管理员使用的工具和命令，这些命令和工具通常需要root权限才能使用。
3. /etc：该文件夹存放的是系统中的配置文件，包括系统全局的配置文件和各种应用程序的配置文件。
4. /dev：该文件夹存放的是设备文件，包括硬件设备和虚拟设备。
5. /usr：该文件夹存放的是用户安装的软件和应用程序，包括可执行文件、库文件、头文件等。
6. /var：该文件夹存放的是系统运行时产生的各种文件，例如日志文件、缓存文件、邮件存储文件等。
7. /proc：该文件夹是一个虚拟文件系统，包含了系统内核和进程的信息。
8. /root：该文件夹是root用户的家目录。
9. /home：该文件夹存放的是普通用户的家目录。
10. /tmp：该文件夹存放的是临时文件，这些文件随时可能被删除。 除了以上列举的文件夹之外，还有其他一些文件夹，例如/boot、/lib、/opt等。不同的文件夹在Linux系统中有着不同的作用，理解各个文件夹的作用可以帮助我们更好地管理和使用Linux系统。
11. /boot文件夹是Linux系统中的一个重要文件夹，其作用是存放系统启动所需的文件。具体来说，/boot文件夹中通常包含以下文件：
    1. 内核文件（vmlinuz）：内核文件是Linux系统中最重要的文件之一，它包含了操作系统内核的所有代码和数据。
    2. 初始化RAM磁盘（initrd）：初始化RAM磁盘是一个虚拟文件系统，用于在系统启动时提供必要的驱动程序和文件系统支持。
    3. 启动加载程序（grub）：启动加载程序是Linux系统启动时的引导程序，它负责加载内核和initrd文件，并启动操作系统。 /boot文件夹通常位于根目录的顶层，它包含了系统启动所需的所有文件，是系统启动的重要组成部分。在Linux系统中，如果/boot文件夹的空间不足，可能会导致系统无法正常启动。因此，管理/boot文件夹的空间是系统管理的一个重要任务。



# 快捷键

### 1. FinalShell里的快捷键

`ctrl + L`:	终端内清屏【clear命令同样可以】

`ctrl + c`:	停止命令的输出结果

`ctrl + d`:	退出或登出账号，或者退出某些特定程序的专属页面（如进入python），<mark>不能用于vi/vim</mark>

`!命令前缀`:	自动执行上一次匹配前缀的命令

`ctrl + r`:	输入内容去匹配历史命令

`ctrl + a`:	跳到命令开头

`ctrl + e`:	跳到命令结尾

`ctrl + 键盘左键`:	向左跳一个单词

`ctrl + 键盘右键`:	向右跳一个单词

### 2. Linux里的快捷键

`ctrl + L`:	终端内清屏【clear命令同样可以】

`ctrl + c`:	强制停止命令，也可以用于输错命令想要直接取消停止

`ctrl + d`:	退出或登出账号，或者退出某些特定程序的专属页面（如进入python），<mark>不能用于vi/vim</mark>

`!命令前缀`:	自动执行上一次匹配前缀的命令

`ctrl + r`:	输入内容去匹配历史命令



# ip地址与主机名

如无法使用ifconfig命令，可以安装：`yum -y install net-tools`

1. 0.0.0.0，特殊IP地址
   ·可以用于指代本机
   ·可以在【端口绑定】中用来确定【绑定关系】（后续讲解）
   ·在一些IP地址限制中，表示所有IP的意思，如【放行规则】设置为0.0.0.0，表示【允许任意IP】访问

**查看主机名指令：**`hostname`

**修改主机名指令（需root）：**`hostnamectl set-hostname 主机名`

**域名解析：**（主机名映射IP地址）

![image-20230316172118719.png](https://s2.loli.net/2023/05/06/rfFhgqmCXPu7Ai8.png)

即：

1. 先查看本机的记录（私人地址本）
   Windows看：**C\Windows\System32\drivers\etc\hosts**
   Linux看：**/etc/hosts**
2. 再联网去DNS服务器（如114.114.114.114，8.8.8.8等）询问

**配置本地域名解析：**

1. windows中以【管理员身份】打开`C\Windows\System32\drivers\etc\hosts`文件，输入格式：`IP地址 域名`

### 配置固定IP

1. 在VMware Workstation（或Fusion）中配置【lP地址网关】和【网段】（IP地址的范围）

   ![image-20230316194340558.png](https://s2.loli.net/2023/05/06/gKrIYW2zZl1HV5E.png)

   ![image-20230316194703773.png](https://s2.loli.net/2023/05/06/Nz2TBkMaVpKnYQh.png)

   ![image-20230316194849392.png](https://s2.loli.net/2023/05/06/Sbgawr8WCR4H32Q.png)

2. 在Linux系统中手动【修改配置文件】，固定lP

   配置方法如下：

   1. 使用vim编辑`/etc/sysconfig/network-scripts/ifcfg-ens33`文件

   2. 修改BOOTPROTO="<mark>static</mark>"（由dhcp改为static）

   3. 新增

      ```bash
      IPADDR="192.168.88.130"		#（Ip地址，可以改后两段数字）
      NETMASK="255.255.255.0"  	#（子网掩码固定：255.255.255.0）
      GATEWAY="192.168.88.2"		#（网关和VMware虚拟网络编辑器中设置的一致）
      DNS1="192.168.88.2"			#（DNS1设置为网关即可）DNS:域名地址解析器
      ```

3. 执行命令`systemctl restart network`重启网卡

   

# 环境变量

**$符号：**在Linux系统中，$符号被用于【取”变量”的值】。环境变量记录的信息，除了给操作系统自己使用外，如果我们想要取用，也可以使用。

```bash
$环境变量名		 #取得环境变量的值
echo $PATH		#取得PATH这个环境变量的值，并通过echo语句输出出来。
echo ${PATH}ABC	#配合环境变量拼接字符串
```

**自行设置环境变量：**

```bash
export 变量名=变量值		#临时设置环境变量
#以下为永久生效方式
·针对当前用户生效，配置在当前用户的：【~/bashrc】文件中
·针对所有用户生效，配置在系统的：【/etc/profile】文件中
source 配置文件			#进行立刻生效，或重新登录FinalShell生效
```

**注意：**`export PATH=$PATH:/home/itheima/myenv`这条指令【切勿】写成~~export PATH=/home/itheima/myenv~~



# MySQL在CentOS系统安装

### MySQL5.7版本

```bash
#更新密钥
rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022

#安装Mysql yum库
rpm -Uvh http://repo.mysql.com//mysql57-community-release-e17-7.noarch.rpm 		#它将会下载并安装MySQL社区版软件源的配置文件。该配置文件描述了如何在yum软件包管理器中访问MySQL社区版的软件包。在安装完该配置文件后，您可以使用yum命令安装MySQL社区版软件包。

#yum安装MysqL
yum -y install mysql-community-server

systemctl start mysqld		#启动
systemctl enable mysqld		#开机自启

systemctl status mysqld		#查看MySQL运行状态

#通过grep命令，在/var/Log/mysqld.1og文件中，过滤temporary password关键字，得到初始密码
grep 'temporary password' /var/log/mysqld.log

mysql -uroot -p		#登录mysql
#解释
#-u，登陆的用户，MySQL数据库的管理员用户同Linux一样，是root
#-p，表示使用密码登陆
#执行完毕后输入刚刚得到的初始密码，即可进入MySQL数据库

#修改mysql root用户密码
ALTER USER 'root'@'localhost' IDENTIFIED BY '密码’;	#一密码需要符合：【大于8位，有大写字母，有特殊符号】，不能是连续的简单语句如123，abc

exit	#退出mysql

netstat -anp | grep 3306	#查看mysql绑定端口，确保无误
```

提示：

1. 如果你想mysql【设置简单密码】，需要降低MysqL的密码安全级别再修改密码(生产环境最好别调)

​		`set global validate_password_policy=LOW;`:	密码安全级别低；<mark>如果是MySQL8.0版本</mark>：`set global validate_password_policy=0;`

​		`set global validate_password_length=4`;:	密码长度最低4位即可

2. 默认情况下，root用户是不允许远程登录的，只允许在MySQL所在的Linux服务器登陆MySQL系统，请注意，允许root远程登录会带来【安全风险】

   >#授权root远程登录
   >`grant all privileges on *.* to root@"IP地址" identified by '密码' with grant option;`
   >
   >#IP地址即允许登陆的IP地址，也可以填写%，表示【允许任何地址】访问
   >#密码表示给远程登录独立设置密码，和本地登陆的密码【可以不同】

   >#刷新权限，生效
   >`flush privileges;`

### MySQL8.0版本

如果已经有了5.7版本，可以执行以下命令：

> rpm -qa | grep -i mysql  （查找出来有哪些）
>
> rpm -ev --nodeps	（用这个删除代码5.0版本） 

```mysql
#安装Mysql8.x版本yum库
rpm -Uvh https://dev.mysql.com/get/mysql80-community-release-e17-2.noarch.rpm	#替换5.7版本的【第五行】代码
```

**与5.7不同的远程登录部分：**

```mysql
#【第一次】设置root远程登录，并配置远程密码使用如下SQL命令
create user 'root'@'%' IDENTIFIED WITH mysql_native_password BY '密码';	#密码需要符合：大于8位，有大写字母，有特殊符号
#【后续修改密码】使用如下SQL命令
ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY '密码'; 	#修改root密码
```



# Tomcat安装部署

[下载JDK软件](https://www.oracle.com/java/technologies/downloads)

**安装步骤如下：**

1. 配置jdk环境

```bash
su - 			#切换root账号
rz				#将windows上下载的JDK上传到Linux上
mkdir -p /export/server		#创建文件夹，用来部署JDK，将JDK和Tomcat都安装部署到：/export/server内
tar -zxvf jdk-8u351-1inux-x64.tar.gz(jdk压缩包名) -C /export/server		#解压缩JDK安装文件
ln -s /export/server/jdk1.8.0_351/export/server/jdk		#配置JDK的软链接

#配置JAVA_HOME环境变量，以及将$JAVA_HOME/bin文件夹加入PATH环境变量中
#编辑/etc/profile文件,内容如下
export JAVA_HOME=/export/server/jdk
export PATH=$PATH:$JAVA_HOME/bin

#生效环境变量
source /etc/profile

#配置java执行程序的软链接
rm -f /usr/bin/java		#删除系统自带的java程序
1n -s /export/server/jdk/bin/java /usr/bin/java		#构建软链接
```

如果需要使用系统自带jdk环境，可以使用如下方式：

```bash
```

2. 解压并部署Tomcat （Tomcat建议使用【非Root用户】安装并启动，可以创建一个用户：tomcat用以部署）

   **须知：**

   >首先，放行tomcat需要使用的8080端口的外部访问权限CentOS系统默认开启了防火墙，阻止外部网络流量访问系统内部
   >所以，如果想要Tomcat可以正常使用，需要对Tomcat默认使用的8080端口【进行放行】
   >放行有2种操作方式：

```bash
#	1.关闭防火墙
#	2.配置防火墙规则，放行端口
#以下操作2选一即可

#方式1：关闭防火墙
systemctl stop firewalld		#关闭防火墙
systemctl disable firewalld	#停止防火墙开机自启

#方式2：放行8080端口的外部访问
firewall-cmd --add-port=8080/tcp --permanent	#【--add-port=8080/tcp】表示【放行】8080端口的tcp访问，【一permanent】表示【永久生效】
firewall-cmd --reload		#重新载入防火墙规则使其生效

#方便起见，建议同学们选择方式1，直接关闭防火墙一劳永逸
#防火墙的配置非常复杂，后面会视情况独立出一集防火墙配置规则的章节。
```

```bash
#以root用户操作，创建tomcat用户
useradd tomcat		#使用root用户操作
passwd tomcat		#【可选】，为tomcat用户配置密码
```

3. 下载并解压Tomcat安装包

```bash
#使用【root用户】操作如下指令
wget https://dlcdn.apache.org/tomcat/tomcat-10/v10.0.27/bin/apache-tomcat-10.0.27.tar.gz
#如果【出现https相关错误】，可以使用一no-check-certificate选项【(不检查http证书)】,如下
wget --no-check-certificate https://dlcdn.apache.org/tomcat/tomcat-10/v10.0.27/bin/apache-tomcat-10.0.27.tar.gz		#如果Linux内下载过慢，可以复制下载链接在Windows系统中使用迅雷等软件加速下载然后上传到Linux内即可或者使用课程资料中提供的安装包

#使用【root用户】操作，否则无权限解压到/export/server内，除非修改此文件夹权限
tar -zxvf apache-tomcat-10.0.27.tar.gz -C /export/server		#解压Tomcat安装包
```

4. 创建Tomcat软链接

```bash
#使用【root用户】操作
ln -s /export/server/apache-tomcat-10.0.27 /export/server/tomcat
```

5. 修改tomcat安装目录权限

```bash
#使用root用户操作，【同时对软链接和tomcat安装文件夹进行修改】，使用通配符*进行匹配
chown -R tomcat:tomcat /export/server/*tomcat*
```

6. 切换到tomcat用户

```bash
su - tomcat
```

7. 启动tomcat

```bash
/export/server/tomcat/bin/startup.sh
```

8. tomcat启动在8080端口，可以检查是否正常启动成功

```bash
netstat -anp | grep 8080
```

