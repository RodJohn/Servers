

# 概述

    web_stomp插件可以让js(做客户端)直接连接rabbitmq(作为STOMP服务器)

# 服务器设置


## 启用插件

  rabbitmq_web_stomp插件随RabbitMQ提供。
  启用插件，rabbitmq-plugins enable rabbitmq_web_stomp

## 设置参数

修改端口号

## 防火墙


# javascript代码


## sockjs

3.7以后不再支持sockjs,而且以前的版本也不稳定(http://www.rabbitmq.com/changelog.html)
但是可以通过spring做中继的方法支持客户端的sockjs


## 库包

STOMP.js

## API


client.subscribe(destination,callback,headers) ：订阅消息 

client.send(destination,headers,body)：发布消息 

client.unsubscribe(id)：取消订阅，id为订阅时返回的编号 

client.onreceive：默认接收回调从临时队列获取消息 

## 示例

```
// 连接STOM端点
// 订阅管道
var client = Stomp.client('ws://127.0.0.1:15674/ws');

var on_connect = function(x) {
    var channel = "/topic/test";
    id = client.subscribe(channel, function(d) {
        console.log("from--"+channel+d.body);
    });
    
};
var on_error =  function() {
    console.log('error');
};

client.connect('guest', 'guest', on_connect, on_error, '/');

//向指定管道发送数据
client.send(channel, {"content-type":"text/plain"}, " my data ");
```

# 参考

官方资料\
http://www.rabbitmq.com/web-stomp.html\

