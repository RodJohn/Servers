
# 参考

    http://www.epinv.com/post/5217.html

# 概述

    VMware Tools，
    能实现主机与虚拟机之间的文件共享，
    也支持自由拖拽的功能，鼠标也可在虚拟机与主机之前自由移动


# linux服务器


    打开“虚拟机”-“设置”-“硬件（CD/DVD）”
    手动加载文件夹(C:\Program Files (x86)\VMware\VMware Workstation)给出的iso文件

    打开VMware Workstation虚拟机，开启CentOS系统
    虚拟机-安装VMware Tools

    登录CentOS终端命令行
    mkdir /media/mnt    #新建挂载目录
    mount /dev/cdrom    /media/mnt/      #挂载VMware Tools安装盘到/media/mnt/目录
    cd /media/mnt/    #进入安装目录
    ll   #查看
    cp    VMwareTools-8.8.1-528969.tar.gz    /home    #复制文件到/home目录
    
    
    tar zxvf VMwareTools-9.6.2-1688356.tar.gz #解压(VMwareTools-9.6.2-1688356.tar.gz这个名称不同的版本是不同的，这里是以VMware 10.03的版本为例)
    cd vmware-tools-distrib   #进入文件目录
    ./vmware-install.pl  #安装
    一直按enter即可
    最后，重启服务器，VMwareTools安装成功。