# mymq

1.  场景：
    * 我们现在有个游戏，已经实现了游戏逻辑，现在需要一个能兼备 可靠，快速，易用 的网络通讯功能， 服务端需要能够很容易扩展；
    * 我们现在有个企业管理软件，需要集成一个公共视频的功能；
    
    
2.  提供：
    * 一个分布式服务端程序
    * 一个 ios 客户端 sdk
    * 一个 android 客户端 sdk
    * 一个 java 客户端 sdk


3.  API:
    * A 发送消息到 群G，不确认； (G会转发给其他成员，但不做确认)(tcp)
    * A 发送消息到 群G，并且确认G收到了；（G一定会把消息转发给其他群成员)
    * A 发送一个协议到 群G；
    * B 同意/反对群G 中来自A 的协议；
    * A 接收群G 成员B 对协议S的结果（同意/反对)；
    * A 发送一个协议到 群G，并且等所有成员全部同意之后，再返回结果；
    * A 创建持久群G；（http
    * A 创建临时群G；（http）
    * A 邀请B加入群G；（http）
    * A 加入群G；（http）
    * A 获取群G的所有成员；（http）

4. API 类别：
    * 消息： 当客户端A成功发数据包给服务端之后，即可继续剩下的逻辑；
    * command： 当客户端A成功发送数据包给服务端之后，需要阻塞并等待服务端反馈消息，才能继续剩下的逻辑；
