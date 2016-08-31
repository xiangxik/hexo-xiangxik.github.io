title: Postgresql使用
date: 2016-07-26 16:25:49
categories: 
- 数据库
tags: 
- 关系数据库

---

Postgresql的安装配置及基本的使用。
<!-- more -->

# 安装及配置

执行以下命令：
```
$ yum install postgresql-server
$ service postgresql initdb
$ chkconfig postgresql on
```

修改配置
```
$ vi /var/lib/pgsql/data/postgresql.conf
```
listen_addresses ='*'

```
$ vi /var/lib/pgsql/data/pg_hba.conf
```


启动：
```
$ service postgresql start
```

修改密码
修改pg_hba.conf文件，访问限制列表method改为trust
```
$ psql -U postgres
$ ALTER USER postgres WITH PASSWORD 'xxx';
```