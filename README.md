# mymq

1.  场景：
    * 我们现在有个游戏，已经实现了游戏逻辑，现在需要一个能轻易扩展出“私聊，世界聊，公会聊”，“广播各种游戏命令（使用技能，购买物品，交易....)” 等功能的网络通讯服务， 并且服务端需要能够很容易平行扩展性能；
    * 我们现在有个企业管理软件，需要集成一个公共视频的功能；
    
    
2.  提供：
    * 一个分布式服务端程序
    * 一个 ios 客户端 sdk
    * 一个 android 客户端 sdk
    * 一个 java 客户端 sdk


3. API 场景(抽象):
    * 
    *    创建一个channel： 通过时间＋机器＋hash（类似mongoId）保证其唯一性
    *    channel 分类： public channel， 任何人可以监听；  private channel 仅私人可以监听；
    *    
    * 一个user 一个连接；
    * 一个user 监听一个channel, 即可收到其他user 发往该 channel 的所有消息；
    * 一个user 有一个私人信箱（private channel)
    * 一个user 可以向另一个user的 private channel, 发消息，例如：邀请，交易； 但不能监听该channel
    * 一个user 向自己的private channel发送任何消息，服务器都只会返回"OK"，而不做任何其他动作；
    * 
    * 消息的属性：
    *    1.    可靠性／不可靠性；  任何消息，都有这两种属性可以选择；
    *    2.    channel；   一条消息一定是发往某个channel的；
    *    3.    sender；    一条消息一定有个发送者，它包括user但不仅限于此， 系统， 世界，等虚拟'user'都可以。


4. API 类别：
    * message： 当客户端A成功发数据包给服务端之后，即可继续剩下的逻辑；
    * command： 当客户端A成功发送数据包给服务端之后，需要阻塞并等待服务端反馈消息，才能继续剩下的逻辑；


5. 客户端架构：
    * socket，  绑定一个专门读取socket数据包的线程 ，该线程将socket内容分发给不同的 channel
    * channel， 共享于多个线程之间；
    * 
