title: Castle开发平台手册
date: 2016-04-24 12:35:39
categories: 
- 架构设计
tags: 
- java

---

Castle Platform的目标是打造一个高性能、高扩展性的java开发平台，完成通用的管理功能。采用了后台管理集中部署，会员业务系统可分离部署等特点，可独立区分后台管理系统、前端展示系统、用户中心系统。开发者可以在此基础上进行扩展，进而使用一个核心就可以开发出各种互联网产品。 
<!-- more -->

<div class="github-widget" data-repo="xiangxik/castle-platform"></div>

# 简介
本平台既适用于开发普通的管理系统，也适用于开发高性能、高扩展性的互联网产品。经过三次大重构，上一版本是https://github.com/xiangxik/java-platform.

## 特点
* 基于目前最新最热门的java技术
* 采用Java8的语法
* 采用servlet3.1规范的集成机制
* 模块可扩展。直接添加或移除对应模块的jar即可。
* 采用spring javaconfig。 达到零spring配置文件。
* 支持多种数据操作混用
* 采用querydsl通用查询
* 包含通用的后台管理
* 可以采用单一服务集成，也可选择地使用第三方服务管理框架（支持dubbo或thrift）。
* 支持javaconfig和kryo序列化的dubbo
* 支持国际化

## 原理说明
采用Dubbo等第三方RMI框架，把业务处理放置于多个Provider， Web服务作为Consumer，对Provider进行调用，从而达到分布式部署。<br/>
![Alt framework](/img/castle/frame.jpg)

## 主要用到的第三方功能
* spring-mvc（MVC框架）
* spring-security（安全框架）
* spring-data（通用数据处理）
* querydsl（通用查询框架）
* jackson（json处理框架）
* infinispan（分布式缓存）
* jpa（关系数据库）
* redis（键值数据库）
* mongodb（文档数据库）
* neo4j（图形数据库）
* groovy-template（碎片化模板）
* thymeleaf（前端模板）
* extjs6（js组件框架）
* dubbo（分布式服务框架）
* thrift（异构系统服务调用框架）

# 开始使用
利用castle-platform的部分jar包的组合，可以构建前端web系统和后端管理web系统，前端可以采用dubbo/thrift/webservice调用后端服务。

## 把例子启动起来

### 1. 配置zookeeper
可查阅http://ken.whenling.com/2016/07/26/zookeeper/ 。配置完成后，启动zookeeper。
![Alt management](/img/castle/zookeeper.jpg)

### 2. 把castle-example引入到eclipse
查看https://github.com/xiangxik/castle-example

### 3. 配置数据库
创建数据库，并且修改工程文件里面的config.properties中的数据库链接。

### 4. 启动管理后台
使用jetty9.3.6+、或者tomcat8.5+ 的容器启动项目 example-management-webapp-extjs.
![Alt management_login](/img/castle/management_login.jpg)
![Alt management](/img/castle/management.jpg)

### 5. 启动Provider
打开example-provider. 打开文件com.whenling.example.provider.support.DubboProviderMain。  
采用java application方式启动。
真实环境采用打包后的/bin/start.sh运行。  

当出现 Dubbo service server started! 表示启动成功。

### 6. 启动website
使用jetty9.3.6+、或者tomcat8.5+ 的容器启动项目 example-management-webapp-extjs.
![Alt website](/img/castle/website.jpg)
