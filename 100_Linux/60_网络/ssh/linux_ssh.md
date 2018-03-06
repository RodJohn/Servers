Linux-ssh


查看当前的ssh版本
Linux一般自带的是OpenSSH: 
$ ssh -V 
OpenSSH_3.9p1, OpenSSL 0.9.7a Feb 19 2003


生成秘钥
输入匹配命令	 ssh-keygen 
Generating public/private rsa key pair.
询问把公钥和私钥放在那里，回车用默认位置即可
Enter file in which to save the key (/root/.ssh/id_rsa): 
输入密码(如果直接回车就是没有)
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
效果
私钥
Your identification has been saved in ./id_rsa.
公钥
Your public key has been saved in ./id_rsa.pub.
指纹
The key fingerprint is:
68:95:a6:98:64:1e:0f:63:75:ae:ca:d7:de:96:ac:ca root@jdu4e00u53f7
图
The key's randomart image is:
+--[ RSA 2048]----+
|      . .        |
|     . o .       |
|    B   =        |
|   = B *         |
|    + * S        |
|   . o .         |
|    o . .. .     |
|     o . .+      |
|      E.oo.      |
+-----------------+

完整命令  ssh-keygen -t rsa -f ~/.ssh/id_rsa -N 'passwd'
    -t指定密钥产生算法
    -f指定生成文件，登陆是使用ssh命令进行的，而他的配置文件默认的私钥为家目录下.ssh/id_rsa
    -N对私钥加密以防止私钥泄露后他人乱用，但这也使得以后每次登陆必须输入-N指定的密码。



权限配置

权限配置很重要，一方面要保证安全，另一方面不能因为权限问题导致自己登陆不成功。
一般用自己的账户在自己的目录下创建.ssh/authorized_keys文件。例如要登陆的账户为XY账户，那么在/home/XY下面创建.ssh目录,然后在.ssh目录下创建authorized_keys文件。其中.ssh文件夹的权限为700，authorized_keys文件的权限为600。






参考
http://blog.csdn.net/qq1436248562/article/details/45854779
http://blog.csdn.net/will5451/article/details/53206776
http://www.ruanyifeng.com/blog/2011/12/ssh_remote_login.html