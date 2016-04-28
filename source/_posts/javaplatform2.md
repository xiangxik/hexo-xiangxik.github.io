title: java平台 2.开始使用
date: 2016-03-19 20:54:44
categories: 
- 架构设计
tags: 
- java

---

<h2 id="intro">开始</h2>要使用一个开发平台，首要事情就是把系统部署起来，并能进行最基本的增删改查。该平台的搭建和进行增删改查是十分的简单的事情。下面我们来一步一步地把系统建立起来。
<!-- more -->

## 环境搭建
* 把代码下载下来并导入到eclipse

![Alt eclipse](/img/javaplatform/2-1.jpg)

* 新建maven工程

![Alt maven](/img/javaplatform/2-2.jpg)

* 修改pom.xml文件

<pre><code>
&lt;project xmlns=&quot;http://maven.apache.org/POM/4.0.0&quot; xmlns:xsi=&quot;http://www.w3.org/2001/XMLSchema-instance&quot;
	xsi:schemaLocation=&quot;http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd&quot;&gt;
	&lt;modelVersion&gt;4.0.0&lt;/modelVersion&gt;
	&lt;parent&gt;
		&lt;groupId&gt;com.whenling&lt;/groupId&gt;
		&lt;artifactId&gt;java-platform&lt;/artifactId&gt;
		&lt;version&gt;1.0.0.RELEASE&lt;/version&gt;
	&lt;/parent&gt;
	&lt;artifactId&gt;example-1&lt;/artifactId&gt;
	&lt;version&gt;1.0.0&lt;/version&gt;
	&lt;packaging&gt;war&lt;/packaging&gt;

	&lt;dependencies&gt;
		&lt;dependency&gt;
			&lt;groupId&gt;com.whenling&lt;/groupId&gt;
			&lt;artifactId&gt;application-centralize&lt;/artifactId&gt;
			&lt;version&gt;1.0.0.RELEASE&lt;/version&gt;
		&lt;/dependency&gt;
	&lt;/dependencies&gt;

	&lt;build&gt;
		&lt;plugins&gt;
			&lt;plugin&gt;
				&lt;groupId&gt;org.apache.maven.plugins&lt;/groupId&gt;
				&lt;artifactId&gt;maven-war-plugin&lt;/artifactId&gt;
				&lt;configuration&gt;
					&lt;!-- web.xml is not mandatory since JavaEE 5 --&gt;
					&lt;failOnMissingWebXml&gt;false&lt;/failOnMissingWebXml&gt;
				&lt;/configuration&gt;
			&lt;/plugin&gt;
		&lt;/plugins&gt;
	&lt;/build&gt;
&lt;/project&gt;
</code></pre>

* 新建初始化器。为了加载自定义的配置文件

<pre><code>
package com.whenling.example1;

import javax.servlet.ServletContext;
import javax.servlet.ServletException;

import org.springframework.core.Ordered;
import org.springframework.core.annotation.Order;
import org.springframework.web.WebApplicationInitializer;

import com.whenling.module.base.config.StaticConfigurationSupplier;

@Order(Ordered.LOWEST_PRECEDENCE)
public class ExampleInitializer implements WebApplicationInitializer {

	@Override
	public void onStartup(ServletContext servletContext) throws ServletException {
		StaticConfigurationSupplier.prepend("config.properties");
	}

}
</code></pre>

* 创建配置文件config.properties

需要相应地创建此数据库。
<pre><code>
jdbc.url=jdbc:mysql://localhost:3306/platform?useUnicode=true&characterEncoding=utf-8
jdbc.username=root
jdbc.password=abcdefg
</code></pre>

* 在webapp下创建WEB-INF文件夹


* 使用支持servlet3.1的容器启动即可
我使用的是jetty-9.3.3.v20150827

## 初步使用
* 输入http://localhost:8080/admin

![Alt eclipse](/img/javaplatform/2-3.jpg)

* 使用初始登陆密码
用户名：admin
密码：asd123

## 总结
整个项目仅仅需要一个初始化器来读取配置文件，即可运行，且拥有了一个完整的后台管理功能。
如要增加功能，只需在pom.xml添加依赖即可。