title: java平台 3.模块化的实现原理
date: 2016-03-19 22:03:21
categories: 
- 架构设计
tags: 
- java

---

<h2 id="intro">开始</h2>各种各样的项目，一些基础总是相同的，如何把基础搭建和巩固起来，使用模块化设计是不错的选择。目前，模块化的产品最规范的是osgi了，不过osgi太过于复杂，而且到现在，各厂商的实现也不能完全的兼容规范。osgi还有个特点是热部署，其实大多数项目，尤其是企业项目，暂停一下服务也不会造成很大的损失。能做到热部署固然是好的，但其增加了项目开发的复杂度，在需求不大的情况下，反而得不偿失。因此，静态模块化的java-platform由此诞生。
<!-- more -->

## java spi
首先，我们需要了解一下java spi。java spi是java6开始，提供的一个jar包之间读取实现类的标准。
主要涉及的类是java.util.ServiceLoader。
只要我们在类路径下的META-INF/services/，创建与接口全名称一样的文件，文件的内容，每一行代表它的一个实现类。
当使用ServiceLoader.load(接口)的时候，java将自动找到所有jar包下面的META-INF/services/接口 文件，加载其描述的实现类。
这样的好处很明显，当一个jar包含有接口的实现类，它的加入，便可以带来的新功能，它的移除，功能也随之移除。功能的添加及移除，不影响任何代码的编写。

## servlet3.1
servlet3.0开始，加入了一个不需要web.xml配置的特性，该特性的实现就是通过spi。
在web项目中，只要在META-INF/services/创建文件javax.servlet.ServletContainerInitializer，在项目中实现该接口，并把其添加到文件中，则容器启动时，会加载这些实现类。
我们可以在实现类中增加filter，增加servlet，增加listener，基本上web.xml的功能都能在此体现，而且代码编写比xml强多了。

## spring web的支持
spring web根据servlet3.0提供的特性，增加了一个对ServletContainerInitializer的实现。我们从源码中也可以看到：
![Alt spring](/img/javaplatform/3-1.jpg)
实现类为org.springframework.web.SpringServletContainerInitializer
查看源码得知，会交给org.springframework.web.WebApplicationInitializer来处理

## 平台模块化
到此，原理已经很清晰，平台就是通过实现WebApplicationInitializer，实现模块化。