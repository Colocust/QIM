im
========

使用`Swoole4`+`Vue2.0`实现的即时聊天工具。

* 使用`MongoDB`存储数据
* 使用`Redis`存储uid与线程id之间的关系

   
扩展
---- 
需要`Swoole-4.4.7`或更高版本

    pecl install swoole
   
需要`MongoDB-4.2.1`或更高版本

    pecl install mongodb
    
需要`Redis-5.0.2`或更高版本

    pecl install redis
    
启动WebSocket服务
---- 
    php WebSocketServer.php
    
步骤
---
    1、用户id与线程id的绑定，我在这里使用的
    redis集合来实现的。WebSocket连接成功后
    会向Server传一个uid，此时便与线程id进行
    绑定。代码可参考WebSocketServer类中的
    onOpen方法。
    
    2、在消息发送成功后Client会自行更新消息
    列表,Server触发onMessage事件后会向redis
    拿指定用户(该消息的接收者)的线程id并进行
    push操作。代码可参考WebSocketServer类中
    的onMessage方法。
    
    3、Client触发onmessage事件后会拿到消息内
    容并更新本地消息列表。
    
End
--- 
    为什么要做这个？
    
    长连接一直是我的一个心结。
    
    大三第一次实习时,Boss让我做一个类似头脑
    王者的小游戏.而当时的我根本算不上一个
    programmer,不具备任何独立解决问题的方法
    以及思路,就这样折腾了1个多月也毫无进展,再
    加上那会儿心态上的不成熟,那次实习也给我留
    下了较大阴影。就这样,长连接成为了我必须攻
    克的技术。快两年过去了(准确说应该是快两年
    后才想起来还有这么一回事儿),终于还是做了
    个小demo出来。
    
    这个demo吧其实有很多不合理的地方,但由于我
    只是想了却当年的心结, 所以就不打算优化维
    护了。
 
    
   
