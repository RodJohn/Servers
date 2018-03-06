Tcp_wrappers是红帽RHEL7系统中默认已经启用的一款流量监控程序，它能够根据来访主机地址与本机目标服务程序做允许或拒绝操作。
换句话说，Linux系统中其实有两个层面的防火墙，第一种是前面讲到的基于TCP/IP协议的流量过滤防护工具，而Tcp_wrappers服务则是能够对系统服务进行允许和禁止的防火墙，从而在更高层面保护了Linux系统的安全运行。
控制列表文件修改后会立即生效，系统将会先检查允许策略规则文件（/etc/hosts.allow），如果匹配到相应的允许策略则直接放行请求，如果没有匹配则会去进一步匹配拒绝策略规则文件（/etc/hosts.deny）的内容，有匹配到相应的拒绝策略就会直接拒绝该请求流量，如果两个文件全都没有匹配到的话也会默认放行这次的请求流量


https://www.zzidc.com/info/CentOS/682.html
http://blog.csdn.net/IT_DREAM_ER/article/details/52314704