title: CentOS6.5基本配置
date: 2016-02-28 21:50:09
tags: linux
---

本文主要列出了CentOS6.5安装之后，需要部署项目要进行的一些基本的操作。下文所述的操作都是本人亲自测试可用的，而且都是十分方便简单的方法。
<!-- more -->
本文有很多处是从网上查找记录下来的，只为方便自己不用再东找西找。如作者有版权要求的，可直接联系本人，本人马上删除其部分内容。

## 安装最新版本的Java
### 1.下载最新版本的java
下载地址：http://www.oracle.com/technetwork/java/javase/downloads/index.html
可得文件：jdk-8u73-linux-x64.rpm

### 2.上传到CentOS的某个目录下

### 3.检查系统原有版本
java version
如无任何版本，则直接进行第6步

### 4. 查看jdk信息
[root@kxx ~]# rpm - qa | grep java
tzdata-java-2014g-1.el6.noarch
java-1.6.0-openjdk-1.6.0.0-11.1.13.4.el6.x86_64
java-1.7.0-openjdk-1.7.0.65-2.5.1.2.el6_5.x86_64

### 5.卸载原有jdk
[root@kxx ~]# rpm -e --nodeps tzdata-java-2014g-1.el6.noarch
[root@kxx ~]# rpm -e --nodeps java-1.6.0-openjdk-1.6.0.0-11.1.13.4.el6.x86_64
[root@kxx ~]# rpm -e --nodeps java-1.7.0-openjdk-1.7.0.65-2.5.1.2.el6_5.x86_64

### 6.安装jdk
[root@kxx ~]# rpm -ivh jdk-8u73-linux-x64.rpm

### 7.验证是否安装成功
[root@kxx ~]# java -version
java version "1.8.0_73"
Java(TM) SE Runtime Environment (build 1.8.0_73-b02)
Java HotSpot(TM) 64-Bit Server VM (build 25.73-b02, mixed mode)

## 安装mysql
### 1.使用yum命令，安装mysql服务端
[root@kxx ~]# yum-y install mysql-server

### 2.设置开机启动
[root@kxx ~]# chkconfig mysqld on

### 3.启动mysql服务
[root@kxx ~]# service mysqld start

### 4.设置mysql的root用户密码
[root@kxx ~]# mysql -u root
mysql>select user,host,password from mysql.user;
mysql>set password for root@localhost=password('asd123');
mysql>exit;

### 5.有密码时登录
[root@kxx ~]# mysql -u root -p

### 6.设置访问权限
mysql>GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'qwe123' WITH GRANT OPTION;
mysql>FLUSH PRIVILEGES;

### 7.基本命令
show databases; //查看所有数据库
use databasename; //使用某个数据库
drop database databasename; //删除某个数据库
exit; //退出数据库连接
create database databasename; //创建数据库
show tables; //列出数据库下所有的表