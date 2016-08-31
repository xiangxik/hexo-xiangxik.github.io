title: Redis使用
date: 2016-07-26 11:55:49
categories: 
- 数据库
tags: 
- nosql

---

Redis的安装配置及基本的使用。
<!-- more -->

# 安装及配置

执行以下命令：
```
$ wget http://download.redis.io/releases/redis-3.2.1.tar.gz
$ tar xzf redis-3.2.1.tar.gz
$ cd redis-3.2.1
$ make
```

修改redis.conf
```
requirepass XXX
bind 内网ip 公网ip
daemonize yes
```

启动：
```
src/redis-server redis.conf
```

测试：
```
$ src/redis-cli
$ > auth XXX
$ 
$ shutdown
```
