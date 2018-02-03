概述

队列（Queue），是缓存消息


声明

由于生产者和消费者都可以通过queue.declare创建队列,
但是由于如果消息路由到了不存在的队列RabbitMQ会直接忽略它们,所以最好是生产者和消费者都建队列


队列名
创建队列时,最好指定一个队列名称,消费者订阅队列时需要队列名称,并在创建绑定时也需要队列名称,如果不指	定,RabbitMQ会随机分配一个名称作为queue.declare的返回值(常用于构建在AMQP上的RPC应用,此时零时匿名队列很有用),
exclusive
创建队列时exclusive为true时,队列会变为私有,此时只有你的应用程序才能消费队列消息,
auto-delete
为true时,当最后一个消费者取消订阅(断开连接)的时候,队列就会自动移除,
配合 Auto expire  How long a queue can be unused for before it is automatically deleted (milliseconds).
Message TTL
How long a message published to a queue can live before it is discarded (milliseconds).
durability
持久化
passive
如果尝试声明一个已经存在的队列时,RabbitMQ就什么都不做,并成功返回,
如果你只是为了检测队列是否存在,可设置queue.declare的passive为true,如果存在会成功返回,否则会直接返回一个错误
Dead letter exchange
Optional name of an exchange to which messages will be republished if they are rejected or expire.
Dead letter routing key
Optional replacement routing key to use when a message is dead-lettered. If this is not set, the message's original routing key will be used
