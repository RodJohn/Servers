连接/信道

连接(Connections)
信道(Channels)

在应用程序和Rabbit代理服务器之间创建一条TCP连接，一旦TCP连接打开，应用程序就可以创建一条AMQP信道。信道是建立在“真实的”TCP连接内的虚拟连接。AMQP命令都是通过信道发送出去的。每条信道都会被指派一个唯一的ID。不论是发送消息，订阅队列货接收消息，这些动作都是通过信道完成的。



消息


(Message)是AMQP通信的基本因素。
消息由Header和Body组成。与TCP/IP协议类似，Header包含的是各种属性信息，Body是真正传输的数据。



生产者