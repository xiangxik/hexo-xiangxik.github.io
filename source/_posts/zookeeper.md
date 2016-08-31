title: ZooKeeper使用
date: 2016-07-26 17:48:49
categories: 
- 工具
tags: 
- java

---

ZooKeeper的安装配置及基本的使用。
<!-- more -->

# 安装及配置

执行以下命令：
```
$ wget http://mirrors.cnnic.cn/apache/zookeeper/zookeeper-3.4.8/zookeeper-3.4.8.tar.gz
$ tar –xf zookeeper-3.4.8.tar.gz
$ cd zookeeper-3.4.8
$ cp conf/zoo_sample.cfg conf/zoo.cfg
$ bin/zkServer.sh start
```