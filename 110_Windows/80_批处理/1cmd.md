






先使用tasklist 命令查看当前系统中的进程列表，然后针对你要杀的进程使用taskkill命令
tasklist /fi "imagename eq nginx.exe"


如要杀nginx.exe进程，命令如下：
taskkill /im nginx.exe /f

 

NOTE: /f在这里意为强制结束进程

 

也可以使用pid杀：

taskkill /pid {pid}




# 使用复制黏贴

http://blog.csdn.net/crazygolf/article/details/37907511