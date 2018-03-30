

# 3 yum源

作用

    就是yum的软件资源库
    
用法    

    可以同时配置多个资源库(Repository),并通过插件自动选择最快的源


## 3.3 查看

    查看当前yum源列表
    yum repolist


## 3.5 添加


### 3.5.1 常用源的添加

#### epel 

简介

    软件多

方案一

    1.打开 http://mirrors.kernel.org/fedora-epel/
    2.根据 需要获取rpm包的url(一般后缀.noarch.rpm)
    3.安装 rpm -Uvh ........

方案二

    yum install epel-release

#### 163

简介
    
    网易（163）yum源是国内最好的yum源之一 ，无论是速度还是软件版本，都非常的不错。
    
方案
    
    cd  /etc/yum.repos.d/
    wget http://mirrors.163.com/.help/CentOS6-Base-163.repo
    参考  http://mirrors.163.com/.help/centos.html
    
    
    


# fastestmirror

 
由于yum中有的mirror速度是非常慢的，如果yum选择了这个mirror，这个时候yum就会非常慢，
对此，可以下载fastestmirror插件，它会自动选择最快的mirror： 

#yum install yum-fastestmirror 
配置文件：（一般不用动）/etc/yum/pluginconf.d/fastestmirror.conf 
你的yum镜像的速度测试记录文件：/var/cache/yum/timedhosts.txt     