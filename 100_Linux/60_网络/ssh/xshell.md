生成/查看秘钥

1.打开Xshell，在菜单栏点击“tools”，在弹出的菜单中选择“User Key Generation Wizard...”(密钥生成向导)


2.在“Key Type”项选择“RSA”公钥加密算法，“Key Length”选择为“1024”位密钥长度


3.点击“Next”，等待密钥生成：



4.继续下一步，
在“Key Name”中输入Key的文件名称；
在“Passphrase”处输入一个密码用于加密私钥，并再次输入密码确认
(可以不输入)


5.点击“Save as file...”按钮，将公钥(Public key)保存到磁盘，文件名为“**.pub”


6.查看秘钥信息
1.点击-工具--用户秘钥管理者
2.选择相应的秘钥,点击属性
3.查看相应的指纹,加密方式,公钥,并且可以修改加密


注册公钥

使用到Xshell登录到服务器，进入到“/root/.ssh/”目录，
运行rz命令(如果没有rz命令，运行yum install lrzsz安装)，将key.pub发送到服务器，
然后运行命令(快速命令:cat me.pub >> authorized_keys)，
将公钥(Public Key)导入到“authorized_keys”文件：
***多个公钥之间要换行






密钥登录

1.打开Xshell，点击“New”按钮，弹出“New Session Properties”对话框，在“Connection”栏目中，输入刚刚配置好公钥(Public Key)的IP地址和端口，如下图所示：


2.点击左侧的“Authentication”,切换到认证栏目，在“Method”选择“Public Key”认证，用户名输入“root”(公钥是放在root目录下的.ssh文件夹中)，在“User Key”中选择我们刚才生成的私钥“key”,“Passphrase”中输入私钥的加密密码。

