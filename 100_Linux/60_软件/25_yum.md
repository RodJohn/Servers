











暂存

每次在执行完yum命令后，系统都会把需要用到的rpm包放在/var/cache/yum/这个目录下，但下载源的不同还是会放在不同源目录下。

清除暂存中rpm包文件  yum clean packages 
清除暂存中rpm头文件 
#yum clearn headers 
清除暂存中旧的rpm头文件 
#yum clean oldheaders 
清除暂存中旧的rpm头文件和包文件 
#yum clearn 或#yum clearn all 
注:相当于yum clean packages + yum clean oldheaders 




# 6 使用


## 6.1 查找/查看

yum search <keyword>
yum search all <keyword>
yum list | grep  <keyword>
根据关键字查找RPM安装包
yum info package1 

#显示安装包信息package1

yum list installed  | grep 


安装/升级/删除
yum install package1 
安装指定的安装包package1
安装位置是在/bin

yum update package1
 #更新指定程序包package1

yum remove | erase package1 
#删除程序包package1




概述
Yum（全称为 Yellow dog Updater, Modified）
是一个在Fedora和RedHat以及CentOS中的RPM包管理器。
能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软件包。
在CentOS中你可以免费使用yum，但Redhat中只有当你付费后才能使用yum

一般的都会自带,安装#rpm -ivh yum-2.0.4-2.noarch.rpm



配置

yum的配置一般有两种方式，一种是直接配置/etc目录下的yum.conf文件，另外一种是在/etc/yum.repos.d目录下增加.repo文件。

/etc/yum.conf 
[main]
cachedir=/var/cache/yum         #yum下载的RPM包的缓存目录
keepcache=0            		 #缓存是否保存，1保存，0不保存。
debuglevel=2           		 #调试级别(0-10)，默认为2(具体调试级别的应用，我也不了解)。
logfile=/var/log/yum.log            #yum的日志文件所在的位置
exactarch=1             		#在更新的时候，是否允许更新不同版本的RPM包，比如是否在i386上更新i686的RPM包。
obsoletes=1            		 #这是一个update的参数，具体请参阅yum(8)，简单的说就是相当于upgrade，允许更新陈旧的RPM包。
gpgcheck=1            		 #是否检查GPG(GNU Private Guard)，一种密钥方式签名。
plugins=1           			 #是否允许使用插件，默认是0不允许，但是我们一般会用yum-fastestmirror这个插件。
installonly_limit=3        		 #允许保留多少个内核包。
exclude=selinux*       		  #屏蔽不想更新的RPM包，可用通配符，多个RPM包之间使用空格分离。

/etc/yum.repos.d




概述

很多Linux开发商提供了线上升级策略。这种策略的实施过程是系统先制作这些相依属性的软件列表，在安装某个软件包的时候，先到这个列表去找，同时与系统内已安装的软件相比较。这样没安装的相依软件就能一次性全部安装起来。哈哈，原版光盘就只有第一次安装时需要用到而已，其他时候只要有网络都可以从开发商的服务器中获得！
不同Linux开发商采用的工具不同，dpkg管理机制出现了 APT 线上升级机制，而RPM 根据开发商的不同所采用工具也不一样，其中有 Red Hat 系统的yum ，SUSE系统的Yast Online Update（YOU），Mandriva的urpm软件等。首先我们结合下面的yum机制示意图来理解线上升级策略。


yum

概述
Yum（全称为 Yellow dog Updater, Modified）
是一个在Fedora和RedHat以及CentOS中的RPM包管理器。
能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软件包。
在CentOS中你可以免费使用yum，但Redhat中只有当你付费后才能使用yum

一般的都会自带,安装#rpm -ivh yum-2.0.4-2.noarch.rpm


/etc/yum.conf 
[main]
cachedir=/var/cache/yum         #yum下载的RPM包的缓存目录
keepcache=0            		 #缓存是否保存，1保存，0不保存。
debuglevel=2           		 #调试级别(0-10)，默认为2(具体调试级别的应用，我也不了解)。
logfile=/var/log/yum.log            #yum的日志文件所在的位置
exactarch=1             		#在更新的时候，是否允许更新不同版本的RPM包，比如是否在i386上更新i686的RPM包。
obsoletes=1            		 #这是一个update的参数，具体请参阅yum(8)，简单的说就是相当于upgrade，允许更新陈旧的RPM包。
gpgcheck=1            		 #是否检查GPG(GNU Private Guard)，一种密钥方式签名。
plugins=1           			 #是否允许使用插件，默认是0不允许，但是我们一般会用yum-fastestmirror这个插件。
installonly_limit=3        		 #允许保留多少个内核包。
exclude=selinux*       		  #屏蔽不想更新的RPM包，可用通配符，多个RPM包之间使用空格分离。





fastestmirror 
由于yum中有的mirror速度是非常慢的，如果yum选择了这个mirror，这个时候yum就会非常慢，
对此，可以下载fastestmirror插件，它会自动选择最快的mirror： 

#yum install yum-fastestmirror 
配置文件：（一般不用动）/etc/yum/pluginconf.d/fastestmirror.conf 
你的yum镜像的速度测试记录文件：/var/cache/yum/timedhosts.txt 



查找/查看

yum search <keyword>
yum search all <keyword>
yum list | grep  <keyword>
根据关键字查找RPM安装包
yum info package1 
#显示安装包信息package1

yum list installed  | grep 


安装/升级/删除
yum install package1 
安装指定的安装包package1
安装位置是在/bin

yum update package1
 #更新指定程序包package1

yum remove | erase package1 
#删除程序包package1


暂存

每次在执行完yum命令后，系统都会把需要用到的rpm包放在/var/cache/yum/这个目录下，但下载源的不同还是会放在不同源目录下。

清除暂存中rpm包文件  yum clean packages 
清除暂存中rpm头文件 
#yum clearn headers 
清除暂存中旧的rpm头文件 
#yum clean oldheaders 
清除暂存中旧的rpm头文件和包文件 
#yum clearn 或#yum clearn all 
注:相当于yum clean packages + yum clean oldheaders 



参考
http://blog.csdn.net/to_baidu/article/details/52583854