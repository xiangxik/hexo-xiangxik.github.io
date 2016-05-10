title: Infinispan缓存
date: 2016-05-08 11:43:13
categories: 
- 缓存
tags: 
- java

---

<h2 id="intro">开始</h2>Infinispan 是个开源的数据网格平台。
<!-- more -->

# 简介
## 运行环境
Infinispan可以在以下环境中运行：
* Java SE 应用
* 单独的一个应用服务器，把Infinispan作为一个服务启动。（譬如JBoss AS）
* 作为你的应用的一个库，作为应用服务器发布， 和你的应用一起启动。（举个栗子，你可以使用在Tomcat或GlassFish中使用Infinispan）
* 在OSGI运行环境中（例如Apache Karaf）

## 模式
Infinispan提供四种操作模式，决定了如何存储数据和把数据存放到哪里。
* 本地（Local)，实体只存储在本地节点，不管是否在集群里面。在这个模式，Infinispan就像本地缓存那样操作。
* 失效（Invalidation），所有的实体只存放在缓存仓库（例如数据库），当一个节点加载数据时，将会从仓库取得。在这个模式，Infinispan就像一个分布式缓存那样操作，
* 复制（Replication），所有数据将会复制到所有节点。在这个模式，Infinispan就像操作一个数据网格或者临时数据仓库，但不会增加内存空间。
* 分布式（Distribution），数据只分布于某个子节点，在这种模式下Infinispan的通常是作为一个数据网格，并且内存相应增加了。

## 交互
Infinispan提供2种访问模式， 都可以运用于任何的运行环境：
* 内嵌在你的应用代码中
* 作为一个远程的服务给客户端调用（支持REST, memcached、Hot Rod wire协议）

# 下载和安装Infinispan
要运行Infinispan，你必须符合以下条件：
* jdk1.8+ （OpenJDK、Oracle Java SE、Oracle JRockit皆可）
* maven 3.2+，如果你使用maven来构建你的项目

## 下载Infinispan
maven:
<pre><code>
&lt;dependency&gt; 
	&lt;groupId&gt;org.infinispan&lt;/groupId&gt; 
	&lt;artifactId&gt;infinispan-embedded&lt;/artifactId&gt; 
	&lt;version&gt;8.2.0.Final&lt;/version&gt; 
&lt;/dependency&gt;
</code></pre>




