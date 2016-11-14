title: 流式WebSocket
date: 2016-08-29 17:25:49
categories: 
- 工具包
tags: 
- java

---

所谓流式WebSocket，指的是把对websocket的处理，转化为类似http处理的方式。即spring-websocket的使用类似于spring-webmvc。  
消息的订阅相当于增加了一个controller，当客户端发布一个topic时，即会转入controller进行处理。
<!-- more -->

原始版本参考：http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#websocket-stomp
