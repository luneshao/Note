# tcp三次握手和四次挥手

[原文链接1](https://blog.csdn.net/qzcsu/article/details/72861891)

[原文链接2](https://www.cnblogs.com/Andya/p/7272462.html)

## 背景描述

`UDP`，在传送数据前不需要先建立连接，远地的主机在收到UDP报文后也不需要给出任何确认。虽然UDP不提供可靠交付，但是正是因为这样，

省去和很多的开销，使得它的速度比较快，比如一些对实时性要求较高的服务，就常常使用的是UDP。

对应的应用层的协议主要有 DNS,TFTP,DHCP,SNMP,NFS 等。

`TCP`，提供面向连接的服务，在传送数据之前必须先建立连接，数据传送完成后要释放连接。因此TCP是一种可靠的的运输服务，

但是正因为这样，不可避免的增加了许多的开销，比如确认，流量控制等。对应的应用层的协议主要有 SMTP,TELNET,HTTP,FTP 等。

## TCP的概述

TCP把连接作为最基本的对象，每一条TCP连接都有两个端点，这种断点我们叫作套接字（socket），它的定义为端口号拼接到IP地址即构成了套接字，

例如，若IP地址为192.3.4.16 而端口号为80，那么得到的套接字为192.3.4.16:80。
