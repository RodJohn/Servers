

# 概述

    rabbitmq定制了分发模式和destination的关系


# 常用模式

## exchange

特点

    通过指定的交换机队列进行订阅/发布消息，转发器需要手动创建 
    每个客户端分别拥有自己的队列
    队列是自动删除的
    没有队列时,消息被丢失

头信息格式

    destination : /exchange/<name>[/<routing-key>]\
     
订阅
    
    在客户端发出订阅请求以后,
    服务器会在名为<name>的exchange上创建一个独立的,自动删除的队列
    队列和客户端相连
    如果<routing-key>存在,并用其进行交换机队列绑定
    

发送

    使用<routing-key>向名称为<name>的exchange发送消息

## topic

特点

    通过指定的交换机队列进行订阅/发布消息，转发器需要手动创建 
    每个客户端分别拥有自己的队列
    队列是自动删除的
    没有队列时,消息被丢失

头信息格式

    destination : /topic/<name>
     
订阅
    
    在客户端发出订阅请求以后,
    服务器会在名为默认exchange上创建一个独立的,自动删除的队列
    用name进行交换机队列绑定
    队列和客户端相连

发送

    使用<routing-key>向名称为<name>的exchange发送消息
    与exchange的区别在于队列不由stomp自动进行创建，队列不存在失败 

## queue

特点

    通过默认交换机队列进行订阅/发布消息，
    所有客户端共有一个队列(只有一个客户端能获取消息)
    队列是持久的
    没有客户端时,消息在队列(队列不存在则自动创建)中存储

头信息格式

    destination : /queue/<name>
     
订阅
    
    在客户端发出订阅请求以后,
    服务器会在名为默认的exchange上创建一个独立的,持久化的队列
    队列和客户端相连
    

发送

    在客户端发出订阅请求以后,
    服务器会在名为默认的exchange上创建一个独立的,持久化的队列
    队列和客户端相连

### amq.queue
   
    与/queue/queuename的区别在于队列不由stomp自动进行创建，队列不存在失败 


## 其他



/temp-queue/xxx：创建一个临时队列(只能在headers中的属性reply-to中使用)，可用于发送消息后通过临时队列接收回复消息，接收通过client.onreceive 

Queue Properties的支持
需要版本的支持，3.6.0以后大多都可以支持，具体具体参考：http://www.rabbitmq.com/stomp.html 

中文消息无法发送问题
中文消息，stomp协议存在编码的问题，发送不出去，会报错关闭掉。可以对中文消息进行encodeURI(data)，接收消息时decodeURI(d.body)。官网文章中提供，消息编码必须为UTF-8。


# 队列属性


## 消息安全

队列独占

非自动删除/持久化

手动应答

方法

    在使用topic模式时,可以使用'auto-delete':false 让队列不自动删除


## 队列消息过时

    设置ttl ,进入私信队列
    
   
https://github.com/rabbitmq/rabbitmq-stomp/issues/24

# 参考

官方资料\
http://www.rabbitmq.com/stomp.html\




