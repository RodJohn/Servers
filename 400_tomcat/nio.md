


流程

    对tomcat来说，每一个进来的请求(request)都需要一个线程，直到该请求结束。
    如果同时进来的请求多于当前可用的请求处理线程数，额外的线程就会被创建，直到到达配置的最大线程数(maxThreads属性值)。
    如果仍就同时接收到更多请求，这些来不及处理的请求就会在Connector创建的ServerSocket中堆积起来，直到到达最大的配置值(acceptCount属性值)。
    至此，任何再来的请求将会收到connection refused错误，直到有可用的资源来处理它们。
    
    
    maxConnections
    maxThreads决定了同时处理的请求数
    acceptCount则决定了有多少请求可等待处理。
    connectionTimeout
    
    


tomcat的http connector有三种：bio、nio、apr
windows，所以tomcat默认使用的是aprconnector
在linux上，默认使用的是bio connector。与nio相比，bio性能较低。




nio 模型

https://blog.csdn.net/kobejayandy/article/details/47810201

