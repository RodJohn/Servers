


#安装

　1.首先创建目录，否则可能报错：mkdir /etc/rabbitmq
    2.启用插件：/sbin/rabbitmq-plugins enable rabbitmq_management
    3.开启端口15672的防火墙
    4.然后访问http://localhost:15672即可,
默认用户guest 密码guest
默认用户只可在localhost上连至/且有全部权限
    5.开启远程访问
　　默认网页是不允许访问的，需要增加一个用户修改一下权限，代码如下：
　　添加用户:rabbitmqctl add_user hxb hxb
　　添加权限:rabbitmqctl set_permissions -p "/" hxb ".*" ".*" ".*"
       修改用户角色rabbitmqctl set_user_tags hxb administrator

  注意：重启服务器后生效。





用户/虚主机

用户
 	新增用户
使用 add a user 功能    
注意 tag的使用
用户管理
直接点击username,可以进入个人资料
修改个人资料,和对应虚主机的权限

虚主机
 新增虚主机
使用 add a new virtrul host 功能    
虚主机管理
直接点击name,可以进入主机管理


交换机
创建交换机
使用Add a new exchange
交换机管理
直接点击name,可以进入管理
修改绑定
发布消息


队列
创建
使用Add a new queue
管理
直接点击name,可以进入管理
查看概况
消息状况
修改绑定
发布消息
(就相当于最简模式发送的)
查询消息  
特别注意
不选择requeue,消息将被消费;选择requeue,消息将重新传递到原先队列,但是会被截断和重新编码
清除消息
使用purge,清除该队列中全部消息