

# docker设置

## win10 

如果你没用使用Docker Machine来管理虚拟机的需求的话,我们

使用默认的Docker守护进程就OK了，不过在此之前我们还需要设置一下docker    
    
打开win10docker活动图标,
选择setting--> general --> 勾选 expose daemon 

将docker与本地的连接设置为不需要TLS加密。

## linux 


# idea设置

## 安装插件

    安装 Docker Integration插件
    
## 设置docker服务

功能页面

    setting --> docker --> 选择+添加docker主机

设置
    
    1.win10本地 ,选择tcp socket ,和默认url ,无需证书文件
    
    
    
设置成功可以看到connection successful 字样    
    
        
    




# 参考

http://blog.csdn.net/chenhaifeng2016/article/details/54315472
http://blog.csdn.net/lovelife527386108/article/details/51697081
https://www.cnblogs.com/hei12138/p/ideausedocker.html