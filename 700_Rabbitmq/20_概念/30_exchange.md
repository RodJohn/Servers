概述

交换器接受来自生产者的消息，并根据不同路由算法将消息发送到消息队列
具体的流程
生产者会把消息(标签和负荷)发送给Exchange，
Exchange决定将消息分发送给某些队列，或者直接丢弃掉,不做保存;
分发的规则主要由exchange的类型和exchange和queue通过routing-key,消息标签中的routing-key.决定





routing-key

producer deliver消息的时候会把routing-key add到 message header中。routing-key只是一个messgae的attribute。


Binding

exchange和queue之间的通过routing-key的关联叫做bingding.
exchange和queue之间的bingding关系很灵活(甚至一对一之间可以多次绑定)


分发

Exchange决定将消息分发送给某些队列，或者直接丢弃掉。

分发的规则主要由exchange的类型和exchange和queue通过routing-key,消息标签中的routing-key.决定


Exchange-Type
交换机有四种类型：Direct, topic, Headers and Fanout


Direct 

如果消息标签中的routing-key等于exchange和queue绑定的routing-key
则该条消息的将被发送到这个queue中

Default Exchange
这种是特殊的Direct Exchange，是rabbitmq内部默认的一个交换机。该交换机的name是空字符串，所有queue都默认binding 到该交换机上。所有binding到该交换机上的queue，routing-key都和queue的name一样。

Topic 

 在这种交换机下，队列和交换机的routing-key是一个匹配规则，
一条消息的routing-key如果符合这个规则,那么这条消息将被分发到这个queue中。

匹配规则
路由键必须是一串字符，用句号（.） 隔开，
比如说 agreements.us，或者 agreements.eu.stockholm 等。
路由模式中可以使用通配
星号（*），主要用于匹配路由键指定位置的一个单词，
井号（#）就表示相当于一个或者多个单词，
举例
满足a.*.c的routing-key有a.hello.c；
满足#.hello的routing-key有a.b.c.helo。

Fanout 

扇形交换机，该交换机会把消息发送到所有binding到该交换机上的queue。
这种是publisher/subcribe模式。用来做广播最好。
所有该exchagne上指定的routing-key都会被ignore掉。

Headers

headers 也是根据规则匹配, 相较于 direct 和 topic 固定地使用 routing_key , headers 则是一个自定义匹配规则的类型.
在队列与交换器绑定时, 会设定一组键值对规则, 消息中也包括一组键值对( headers 属性), 当这些键值对有一对, 或全部匹配时, 消息被投送到对应队列.

