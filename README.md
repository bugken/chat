1.项目C++实现集群聊天服务器
    本项目要实现一个高性能的聊天服务器的开发，主要涉及到的热点技术为高并发和网络编程。首先做一个单机版的聊天服务器，然后扩展成聊天服务器集群。集群中一个重要的技术就是负载均衡。

2.主要技术
    2.1muduo网络库
        muduo网络编程，muduo网络库的多线程编程模型，
    2.2nginx配置tcp负载均衡
    2.3服务器中间件Redis
        基于Redis的发布-订阅模式，实现消息队列，服务器集群基于Redis消息队列进行通讯
    2.4MySQL数据库编程
    2.5json序列化和反序列化
        网络服务器和客户端之间通讯需要序列化和反序列化技术，实现序列化和反序列化的技术很多，有protobuf、xml、json，在这个项目中使用json对数据进行序列化和反序列化。
    2.6CMake构建编译环境

3.项目功能
    3.1客户端新用户注册
    3.2客户端新用户登录
    3.3添加好友和添加群组
    3.4群组聊天

4.项目目标
    4.1掌握服务器的网络I/O模块、业务模块、数据库模块的分层涉及思想
        将模块进行分层设计比较好，当前I/O模块使用的是muduo网络库，如果不想使用它，可以使用libevent库进行替换，业务模块使用的是json进行序列化和反序列化，以后可以使用protobuf替换，数据库模块也可以替换为SQLServer等。这样各个模块之间解耦，单个模块升级或者更新技术不会影响到其他模块。
    4.2掌握C++muduo网络库的编程以及实现原理
    4.3掌握Json的编程应用
    4.4掌握nginx配置部署tcp负载均衡的应用以及原理
    4.5掌握服务器中间件的应用场景和基于发布-订阅的Redis编程实践以及应用原理
    4.6掌握CMake构建自动化编译环境
    4.7掌握GitHub管理项目

5.相关概念或者问题
    5.1负载均衡器的作用:
        5.1.1 把client的请求按照负载均衡算法分发到具体业务服务器ChatServer上面;
        5.1.2 能够和ChatServer保持心跳机制,检测ChatServer的故障;
        5.1.3 能够发现新添加的ChatServer设备,方便扩展服务器数量.
    5.2如何解决跨服务器通信问题
        集群部署的服务器之间进行通信，最好的方式就是引入中间件消息队列，解耦各个服务器，使整个系统松耦合，提高服务器的相应能力，节省服务器带宽，经常使用的中间件消息队列由ActiveMQ、RabbitMQ、Kafka和Redis等，他们都是应用场景广泛并且性能很好的消息队列，供集群服务器之间，分布式服务器之间进行消息通信。