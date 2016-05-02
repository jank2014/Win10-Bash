# Win10-Bash
#Windows上运行Linux子系统

#微软做出的改变,这将是下一代开发的方向吗 Win10 bash shell LAMP
####Win10 要支持Linux 了 你知道吗? 我想这是今年微软做出的最大的改变了,作为开发者 Win10 + Linux 你想到了什么?
####一开始觉得很像笑话,但是微软真的这么做了,而且还在不断的稳步改善.一开始我的想法就是如果可行的话 我会把本地的数据库服务器放到Linux上运行.今天我实现了这个功能,真的非常感谢微软.

#分享一下

##环境与软件:
* Macbook Pro 10.11.4
* Parallels Desktop 11.02
* Win10 14332 X64 64位预览版镜像
* KMS10激活软件
* My_WCP_Watermark_Editor_v1.0.1
注意:要64为Win10 才支持Bash
以上只是我自己的配置,你可以到互联网上下载相关软件
##实现功能
PD虚拟机安装Win10
Win10 开启Bash shell
Win10 bash shell 下 安装 LAMP(Apache MySQL PHP)

###PD虚拟机安装Win10
####由于安装比较简单 这里不进行详细说明
把下载好的Win10 14332镜像拷贝到桌面 或者直接放在下载目录下
![GitHub set up](https://github.com/jank2014/Win10-Bash/blob/master/pics/屏幕快照%202016-05-02%20上午5.50.49.png?raw=true)
选择Win10镜像 这里记得点击一下,不然不会自动选择的 .

![选择镜像](https://github.com/jank2014/Win10-Bash/blob/master/pics/屏幕快照%202016-05-02%20上午5.51.11.png?raw=true)
这里 该版本需要提供产品密钥 去掉选择 不要打勾, 下面安装完可以用激活工具激活.	
![](https://github.com/jank2014/Win10-Bash/blob/master/pics/屏幕快照%202016-05-02%20上午5.51.21.png?raw=true)

等待安装完成后 在PD顶部菜单栏选择

####查看>Retina分辨率>最适合Retina
这一步 非常重要,不然你的系统界面会模糊. 全屏效果发现Win10 是个良心系统啊 显示效果和流畅度不差Mac os


####看一下安装完成的效果
![](https://github.com/jank2014/Win10-Bash/blob/master/pics/屏幕快照%202016-05-02%20上午6.05.43.png?raw=true)
####激活系统
管理员运行 HEU_KMS_Activator_v10.0.0.exe


什么都不要管 点击第一项 等1-2 分钟 会有 失败/成功的提示.第一次一般不会成功,失败后不用管再激活一次,一般两次会成功.

![](https://github.com/jank2014/Win10-Bash/blob/master/pics/屏幕快照%202016-05-02%20上午6.07.53.png?raw=true)

###安装Bash
####开启开发者模式 
win10 底栏 最右边 打开通知 选择 所有设置>更新和安全>针对开发人员 
![](https://github.com/jank2014/Win10-Bash/blob/master/pics/屏幕快照%202016-05-02%20上午6.16.17.png?raw=true
)
####开启Linux子系统
#####控制面板\所有控制面板项\程序和功能
![](https://github.com/jank2014/Win10-Bash/blob/master/pics/屏幕快照%202016-05-02%20上午6.23.04.png?raw=true
)
#####打钩 适用于Linux的Windows子系统(Beta)
 
#####这样子基本准备就完成,不过这才刚刚开始
####安装Bash
管理员身份运行 CMD
输入bash
输入Y
按照提示安装
这里可能遇到两问题:
1.乱码 百度解决
2.无法连接商店下载 也就是下载失败

这里多尝试几次,可能服务器不稳定,亲测连续尝试将近10次才开始下载

####下载完成后会提示你创建用户和密码 这里按照提示操作就可以了

然后 输入bash 开启Win bash

jankz@JANKZ839B:/mnt/c/Users/jankz$
从这里可以看出什么?...

####先ls 一下

```
C:\Users\jankz>bashjankz@JANKZ839B:/mnt/c/Users/jankz$ lsls: cannot access Application Data: Input/output errorls: cannot access Cookies: Input/output errorls: cannot access Local Settings: Input/output errorls: cannot access My Documents: Input/output errorls: cannot access NetHood: Input/output errorls: cannot access PrintHood: Input/output errorls: cannot access Recent: Input/output errorls: cannot access SendTo: Input/output errorls: cannot access Templates: Input/output errorls: cannot access 「开始」菜单: Input/output errorAppDataApplication DataContactsCookiesDesktopDocumentsDownloadsFavoritesLinksLocal SettingsMusicMy DocumentsNetHoodNTUSER.DATNTUSER.DAT{4cbafd95-093a-11e6-80d0-f4521496a040}.TM.blfNTUSER.DAT{4cbafd95-093a-11e6-80d0-f4521496a040}.TMContainer00000000000000000001.regtrans-msNTUSER.DAT{4cbafd95-093a-11e6-80d0-f4521496a040}.TMContainer00000000000000000002.regtrans-msntuser.dat.LOG1ntuser.dat.LOG2ntuser.iniOneDrivePicturesPrintHoodRecentSaved GamesSearchesSendToTemplatesVideos
「开始」菜单
```

####根目录看一下 
cd /
ls 

```
jankz@JANKZ839B:/mnt/c/Users/jankz$ cd /jankz@JANKZ839B:/$ lsacct  boot   data  etc   init  lib64       media  opt   root  sbin  sys  usrbin   cache  dev   home  lib   lost+found  mnt    proc  run   srv   tmp  varjankz@JANKZ839B:/$
```
熟悉吧 这个是Ubuntu 系统

####基本了解
* 查看内核:uname -a
* 查看Ubuntu版本:cat /etc/issue
* 查看硬件:lshw

```
jankz@JANKZ839B:/$ uname -aLinux JANKZ839B 3.4.0+ #1 PREEMPT Thu Aug 1 17:06:05 CST 2013 x86_64 x86_64 x86_64 GNU/Linuxjankz@JANKZ839B:/$ cat /etc/issueUbuntu 14.04.4 LTS \n \ljankz@JANKZ839B:/$ lshwWARNING: you should run this program as super-user.jankz839b    description: Computer    width: 64 bits  *-core       description: Motherboard       physical id: 0     *-memory          description: System memory          physical id: 0          size: 1006MiB     *-cpu          product: Intel(R) Core(TM) i5-5257U CPU @ 2.70GHz          vendor: Intel Corp.          physical id: 1          bus info: cpu@0          width: 64 bits          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx rdtscp x86-64 pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave osxsave avx f16c rdrand hypervisor cpufreqWARNING: output may be incomplete or inaccurate, you should run this program as super-user.jankz@JANKZ839B:/$
```
###LAMP安装
建议用root用户安装
设置root密码 sudo passwd root
输入两次密码 即可设置成功.

su root 
输入密码

```
jankz@JANKZ839B:/$ su rootPassword:root@JANKZ839B:/#
```
这样就切换到root用户了
####安装 apache
apt-get install apache2

```
jankz@JANKZ839B:/$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreetype6 os-prober
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-bin apache2-data libapr1 libaprutil1 libaprutil1-dbd-sqlite3
  libaprutil1-ldap ssl-cert
Suggested packages:
  apache2-doc apache2-suexec-pristine apache2-suexec-custom apache2-utils
  openssl-blacklist
The following NEW packages will be installed:
  apache2 apache2-bin apache2-data libapr1 libaprutil1 libaprutil1-dbd-sqlite3
  libaprutil1-ldap ssl-cert
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,283 kB of archives.
After this operation, 5,348 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main libapr1 amd64 1.5.0-1 [85.1 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/main libaprutil1 amd64 1.5.3-1 [76.4 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ trusty/main libaprutil1-dbd-sqlite3 amd64 1.5.3-1 [10.5 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ trusty/main libaprutil1-ldap amd64 1.5.3-1 [8,634 B]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty-updates/main apache2-bin amd64 2.4.7-1ubuntu4.9 [839 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ trusty-updates/main apache2-data all 2.4.7-1ubuntu4.9 [160 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty-updates/main apache2 amd64 2.4.7-1ubuntu4.9 [87.5 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ trusty/main ssl-cert all 1.0.33 [16.6 kB]
Fetched 1,283 kB in 19s (66.2 kB/s)
Preconfiguring packages ...
Can't exec "/tmp/ssl-cert.config.7LuOvT": Invalid argument at /usr/share/perl/5.18/IPC/Open3.pm line 173.
open2: exec of /tmp/ssl-cert.config.7LuOvT configure  failed at /usr/share/perl5/Debconf/ConfModule.pm line 59.
E: Can not write log (Is /dev/pts mounted?) - openpty (2: No such file or directory)
Selecting previously unselected package libapr1:amd64.
(Reading database ... 25011 files and directories currently installed.)
Preparing to unpack .../libapr1_1.5.0-1_amd64.deb ...
Unpacking libapr1:amd64 (1.5.0-1) ...
Selecting previously unselected package libaprutil1:amd64.
Preparing to unpack .../libaprutil1_1.5.3-1_amd64.deb ...
Unpacking libaprutil1:amd64 (1.5.3-1) ...
Selecting previously unselected package libaprutil1-dbd-sqlite3:amd64.
Preparing to unpack .../libaprutil1-dbd-sqlite3_1.5.3-1_amd64.deb ...
Unpacking libaprutil1-dbd-sqlite3:amd64 (1.5.3-1) ...
Selecting previously unselected package libaprutil1-ldap:amd64.
Preparing to unpack .../libaprutil1-ldap_1.5.3-1_amd64.deb ...
Unpacking libaprutil1-ldap:amd64 (1.5.3-1) ...
Selecting previously unselected package apache2-bin.
Preparing to unpack .../apache2-bin_2.4.7-1ubuntu4.9_amd64.deb ...
Unpacking apache2-bin (2.4.7-1ubuntu4.9) ...
Selecting previously unselected package apache2-data.
Preparing to unpack .../apache2-data_2.4.7-1ubuntu4.9_all.deb ...
Unpacking apache2-data (2.4.7-1ubuntu4.9) ...
Selecting previously unselected package apache2.
Preparing to unpack .../apache2_2.4.7-1ubuntu4.9_amd64.deb ...
Unpacking apache2 (2.4.7-1ubuntu4.9) ...
Selecting previously unselected package ssl-cert.
Preparing to unpack .../ssl-cert_1.0.33_all.deb ...
Unpacking ssl-cert (1.0.33) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
WARN: / is group writable!
Setting up libapr1:amd64 (1.5.0-1) ...
Setting up libaprutil1:amd64 (1.5.3-1) ...
Setting up libaprutil1-dbd-sqlite3:amd64 (1.5.3-1) ...
Setting up libaprutil1-ldap:amd64 (1.5.3-1) ...
Setting up apache2-bin (2.4.7-1ubuntu4.9) ...
Setting up apache2-data (2.4.7-1ubuntu4.9) ...
Setting up apache2 (2.4.7-1ubuntu4.9) ...
Enabling module mpm_event.
Enabling module authz_core.
Enabling module authz_host.
Enabling module authn_core.
Enabling module auth_basic.
Enabling module access_compat.
Enabling module authn_file.
Enabling module authz_user.
Enabling module alias.
Enabling module dir.
Enabling module autoindex.
Enabling module env.
Enabling module mime.
Enabling module negotiation.
Enabling module setenvif.
Enabling module filter.
Enabling module deflate.
Enabling module status.
Enabling conf charset.
Enabling conf localized-error-pages.
Enabling conf other-vhosts-access-log.
Enabling conf security.
Enabling conf serve-cgi-bin.
Enabling site 000-default.
runlevel:/var/run/utmp: No such file or directory
invoke-rc.d: policy-rc.d denied execution of start.
Setting up ssl-cert (1.0.33) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
WARN: / is group writable!
```

####安装php5
sudo apt-get install php5

```
jankz@JANKZ839B:/$ sudo apt-get install php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreetype6 os-prober
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libapache2-mod-php5 php5-cli php5-common php5-json php5-readline
Suggested packages:
  php-pear php5-user-cache
The following NEW packages will be installed:
  libapache2-mod-php5 php5 php5-cli php5-common php5-json php5-readline
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,863 kB of archives.
After this operation, 20.5 MB of additional disk space will be used.
Err http://archive.ubuntu.com/ubuntu/ trusty/main php5-json amd64 1.3.2-2build1
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com/ubuntu/ trusty-updates/main php5-common amd64 5.5.9+dfsg-1ubuntu4.16
  Could not resolve 'archive.ubuntu.com'
Get:1 http://security.ubuntu.com/ubuntu/ trusty-security/main php5-common amd64 5.5.9+dfsg-1ubuntu4.16 [445 kB]
Get:2 http://security.ubuntu.com/ubuntu/ trusty-security/main php5-cli amd64 5.5.9+dfsg-1ubuntu4.16 [2,164 kB]
Get:3 http://security.ubuntu.com/ubuntu/ trusty-security/main php5-readline amd64 5.5.9+dfsg-1ubuntu4.16 [12.1 kB]
Get:4 http://security.ubuntu.com/ubuntu/ trusty-security/main libapache2-mod-php5 amd64 5.5.9+dfsg-1ubuntu4.16 [2,207 kB]
Get:5 http://security.ubuntu.com/ubuntu/ trusty-security/main php5 all 5.5.9+dfsg-1ubuntu4.16 [1,306 B]
Fetched 4,829 kB in 2min 7s (37.9 kB/s)
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/php-json/php5-json_1.3.2-2build1_amd64.deb  Could not resolve 'archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
jankz@JANKZ839B:/$
jankz@JANKZ839B:/$ sudo apt-get install php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreetype6 os-prober
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libapache2-mod-php5 php5-cli php5-common php5-json php5-readline
Suggested packages:
  php-pear php5-user-cache
The following NEW packages will be installed:
  libapache2-mod-php5 php5 php5-cli php5-common php5-json php5-readline
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.4 kB/4,863 kB of archives.
After this operation, 20.5 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main php5-json amd64 1.3.2-2build1 [34.4 kB]
Fetched 34.4 kB in 0s (36.9 kB/s)
E: Can not write log (Is /dev/pts mounted?) - openpty (2: No such file or directory)
Selecting previously unselected package php5-json.
(Reading database ... 25654 files and directories currently installed.)
Preparing to unpack .../php5-json_1.3.2-2build1_amd64.deb ...
Unpacking php5-json (1.3.2-2build1) ...
Selecting previously unselected package php5-common.
Preparing to unpack .../php5-common_5.5.9+dfsg-1ubuntu4.16_amd64.deb ...
Unpacking php5-common (5.5.9+dfsg-1ubuntu4.16) ...
Selecting previously unselected package php5-cli.
Preparing to unpack .../php5-cli_5.5.9+dfsg-1ubuntu4.16_amd64.deb ...
Unpacking php5-cli (5.5.9+dfsg-1ubuntu4.16) ...
Selecting previously unselected package php5-readline.
Preparing to unpack .../php5-readline_5.5.9+dfsg-1ubuntu4.16_amd64.deb ...
Unpacking php5-readline (5.5.9+dfsg-1ubuntu4.16) ...
Selecting previously unselected package libapache2-mod-php5.
Preparing to unpack .../libapache2-mod-php5_5.5.9+dfsg-1ubuntu4.16_amd64.deb ...
Unpacking libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.16) ...
Selecting previously unselected package php5.
Preparing to unpack .../php5_5.5.9+dfsg-1ubuntu4.16_all.deb ...
Unpacking php5 (5.5.9+dfsg-1ubuntu4.16) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up php5-json (1.3.2-2build1) ...
php5_invoke: Enable module json for apache2 SAPI
php5_invoke: Enable module json for cli SAPI
Setting up php5-common (5.5.9+dfsg-1ubuntu4.16) ...

Creating config file /etc/php5/mods-available/pdo.ini with new version
php5_invoke: Enable module pdo for apache2 SAPI
php5_invoke: Enable module pdo for cli SAPI

Creating config file /etc/php5/mods-available/opcache.ini with new version
php5_invoke: Enable module opcache for apache2 SAPI
php5_invoke: Enable module opcache for cli SAPI
Setting up php5-cli (5.5.9+dfsg-1ubuntu4.16) ...
update-alternatives: using /usr/bin/php5 to provide /usr/bin/php (php) in auto mode

Creating config file /etc/php5/cli/php.ini with new version
php5_invoke json: already enabled for cli SAPI
php5_invoke opcache: already enabled for cli SAPI
php5_invoke pdo: already enabled for cli SAPI
Setting up php5-readline (5.5.9+dfsg-1ubuntu4.16) ...

Creating config file /etc/php5/mods-available/readline.ini with new version
php5_invoke: Enable module readline for apache2 SAPI
php5_invoke: Enable module readline for cli SAPI
Setting up libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.16) ...

Creating config file /etc/php5/apache2/php.ini with new version
php5_invoke json: already enabled for apache2 SAPI
php5_invoke opcache: already enabled for apache2 SAPI
php5_invoke pdo: already enabled for apache2 SAPI
php5_invoke readline: already enabled for apache2 SAPI
Module mpm_event disabled.
Enabling module mpm_prefork.
apache2_switch_mpm Switch to prefork
runlevel:/var/run/utmp: No such file or directory
invoke-rc.d: policy-rc.d denied execution of restart.
apache2_invoke: Enable module php5
runlevel:/var/run/utmp: No such file or directory
invoke-rc.d: policy-rc.d denied execution of restart.
Setting up php5 (5.5.9+dfsg-1ubuntu4.16) ...
```

####安装MySQL
sudo apt-get install mysql-server mysql-client


```
jankz@JANKZ839B:/$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreetype6 os-prober
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libaio1 libdbd-mysql-perl libdbi-perl libhtml-template-perl libmysqlclient18
  libterm-readkey-perl mysql-client-5.5 mysql-client-core-5.5 mysql-common
  mysql-server-5.5 mysql-server-core-5.5
Suggested packages:
  libclone-perl libmldbm-perl libnet-daemon-perl libplrpc-perl
  libsql-statement-perl libipc-sharedcache-perl tinyca mailx
The following NEW packages will be installed:
  libaio1 libdbd-mysql-perl libdbi-perl libhtml-template-perl libmysqlclient18
  libterm-readkey-perl mysql-client-5.5 mysql-client-core-5.5 mysql-common
  mysql-server mysql-server-5.5 mysql-server-core-5.5
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,005 kB of archives.
After this operation, 97.1 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main libaio1 amd64 0.3.109-4 [6,364 B]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty-updates/main mysql-common all 5.5.49-0ubuntu0.14.04.1 [12.9 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libmysqlclient18 amd64 5.5.49-0ubuntu0.14.04.1 [596 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ trusty/main libdbi-perl amd64 1.630-1 [879 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty/main libdbd-mysql-perl amd64 4.025-1 [99.3 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ trusty/main libterm-readkey-perl amd64 2.31-1 [27.4 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty-updates/main mysql-client-core-5.5 amd64 5.5.49-0ubuntu0.14.04.1 [706 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ trusty-updates/main mysql-client-5.5 amd64 5.5.49-0ubuntu0.14.04.1 [1,468 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ trusty-updates/main mysql-server-core-5.5 amd64 5.5.49-0ubuntu0.14.04.1 [3,288 kB]
Get:10 http://archive.ubuntu.com/ubuntu/ trusty-updates/main mysql-server-5.5 amd64 5.5.49-0ubuntu0.14.04.1 [1,845 kB]
Get:11 http://archive.ubuntu.com/ubuntu/ trusty/main libhtml-template-perl all 2.95-1 [65.5 kB]
Get:12 http://archive.ubuntu.com/ubuntu/ trusty-updates/main mysql-server all 5.5.49-0ubuntu0.14.04.1 [11.3 kB]
Fetched 9,005 kB in 23s (384 kB/s)
Preconfiguring packages ...
E: Can not write log (Is /dev/pts mounted?) - openpty (2: No such file or directory)
Selecting previously unselected package libaio1:amd64.
(Reading database ... 25742 files and directories currently installed.)
Preparing to unpack .../libaio1_0.3.109-4_amd64.deb ...
Unpacking libaio1:amd64 (0.3.109-4) ...
Selecting previously unselected package mysql-common.
Preparing to unpack .../mysql-common_5.5.49-0ubuntu0.14.04.1_all.deb ...
Unpacking mysql-common (5.5.49-0ubuntu0.14.04.1) ...
Selecting previously unselected package libmysqlclient18:amd64.
Preparing to unpack .../libmysqlclient18_5.5.49-0ubuntu0.14.04.1_amd64.deb ...
Unpacking libmysqlclient18:amd64 (5.5.49-0ubuntu0.14.04.1) ...
Selecting previously unselected package libdbi-perl.
Preparing to unpack .../libdbi-perl_1.630-1_amd64.deb ...
Unpacking libdbi-perl (1.630-1) ...
Selecting previously unselected package libdbd-mysql-perl.
Preparing to unpack .../libdbd-mysql-perl_4.025-1_amd64.deb ...
Unpacking libdbd-mysql-perl (4.025-1) ...
Selecting previously unselected package libterm-readkey-perl.
Preparing to unpack .../libterm-readkey-perl_2.31-1_amd64.deb ...
Unpacking libterm-readkey-perl (2.31-1) ...
Selecting previously unselected package mysql-client-core-5.5.
Preparing to unpack .../mysql-client-core-5.5_5.5.49-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-client-core-5.5 (5.5.49-0ubuntu0.14.04.1) ...
Selecting previously unselected package mysql-client-5.5.
Preparing to unpack .../mysql-client-5.5_5.5.49-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-client-5.5 (5.5.49-0ubuntu0.14.04.1) ...
Selecting previously unselected package mysql-server-core-5.5.
Preparing to unpack .../mysql-server-core-5.5_5.5.49-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-server-core-5.5 (5.5.49-0ubuntu0.14.04.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up mysql-common (5.5.49-0ubuntu0.14.04.1) ...
top - 21:02:37 up 27 min,  0 users,  load average: 0.52, 0.58, 0.59
Tasks:   3 total,   1 running,   2 sleeping,   0 stopped,   0 zombie
%Cpu(s):  5.3 us, 51.9 sy,  0.0 ni, 42.6 id,  0.0 wa,  0.1 hi,  0.0 si,  0.0 st
KiB Mem:   1031052 total,   350316 used,   680736 free,        0 buffers
KiB Swap:        0 total,        0 used,        0 free.        0 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
    1 root      20   0       0      0      0 S   0.0  0.0   0:00.00 init
    2 jankz     20   0       0      0      0 S   0.0  0.0   0:00.96 bash
 6194 jankz     20   0       0      0      0 R   0.0  0.0   0:00.01 top
```


##测试

测试数据库

```
root@JANKZ839B:/# mysql -uroot -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 46
Server version: 5.5.49-0ubuntu0.14.04.1 (Ubuntu)

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
+--------------------+
3 rows in set (0.00 sec)

mysql> CREATE DATABASE jzopen;
Query OK, 1 row affected (0.01 sec)

mysql> use jzopen;
Database changed
mysql> CREATE TABLE IF NOT EXISTS user(
    -> id INT NOT NULL AUTO_INCREMENT KEY,
    -> username VARCHAR(20) NOT NULL);
Query OK, 0 rows affected (0.02 sec)

mysql> SHOW TABLES;
+------------------+
| Tables_in_jzopen |
+------------------+
| user             |
+------------------+
1 row in set (0.00 sec)

mysql> DESC user;
+----------+-------------+------+-----+---------+----------------+
| Field    | Type        | Null | Key | Default | Extra          |
+----------+-------------+------+-----+---------+----------------+
| id       | int(11)     | NO   | PRI | NULL    | auto_increment |
| username | varchar(20) | NO   |     | NULL    |                |
+----------+-------------+------+-----+---------+----------------+
2 rows in set (0.00 sec)

mysql> ALTER TABLE user ADD password VARCHAR(32) NOT NULL;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC user;
+----------+-------------+------+-----+---------+----------------+
| Field    | Type        | Null | Key | Default | Extra          |
+----------+-------------+------+-----+---------+----------------+
| id       | int(11)     | NO   | PRI | NULL    | auto_increment |
| username | varchar(20) | NO   |     | NULL    |                |
| password | varchar(32) | NO   |     | NULL    |                |
+----------+-------------+------+-----+---------+----------------+
3 rows in set (0.01 sec)

mysql> EXIT;
```
###测试服务器 php 

```root@JANKZ839B:/etc# cd ..
root@JANKZ839B:/# cd /var/www/
root@JANKZ839B:/var/www# ls
html
root@JANKZ839B:/var/www# cd html/
root@JANKZ839B:/var/www/html# ls
index.html
root@JANKZ839B:/var/www/html# vim phpinfo.php
root@JANKZ839B:/var/www/html# cat phpinfo.php
<?php
phpinfo();
?>
root@JANKZ839B:/var/www/html# tree
.
├── index.html
└── phpinfo.php
```
 win10访问 127.0.0.1
 
![](https://github.com/jank2014/Win10-Bash/blob/master/pics/屏幕快照%202016-05-02%20上午7.19.01.png?raw=true)
 win10访问 127.0.0.1/phpinfo.php
 
![](https://github.com/jank2014/Win10-Bash/blob/master/pics/屏幕快照%202016-05-02%20上午7.20.31.png?raw=true)


##思考


