title: java平台 4.混合式配置
date: 2016-03-19 22:23:13
categories: 
- 架构设计
tags: 
- java

---

<h2 id="intro">开始</h2>配置是每一个框架最基本的部分，java-platform也不例外。本平台分静态配置和动态配置，静态配置指的是需要重启才会生效的配置，动态配置是能在界面上修改且即时生效的配置。
<!-- more -->

## apache configuration

平台主要使用的配置框架是apache configuration，由它提供了统一的Configuration接口。

## 静态配置
* 利用apache configuration工具，得出静态配置类:
com.whenling.module.base.config.StaticConfigurationSupplier
其append和prepend方法可以添加配置文件。
支持的配置文件类型有：xml(层次关系较好)、plist(可以带类型)、properties(常用简单)


* 加载周期
静态配置应该是在系统启动最初的时候加载，故在org.springframework.web.WebApplicationInitializer的onStartup方法中加载是最好不过的了。


* 加载顺序
当两个配置相同的时候，平台会使用最先找到的那一项。


* 与spring配置混合
在ConfigConfiguration中，ConfigurationPropertySourcesPlaceholderConfigurer已做了混合的支持，即可以spring的表达式使用这些配置。


## 动态配置

