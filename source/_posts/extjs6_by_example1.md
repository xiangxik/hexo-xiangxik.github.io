title: 《Ext JS 6 By Example》 章节1. 开始使用
date: 2016-01-30 18:05:16
categories:
- 原创翻译
tags: 
- extjs

---

当你留意到这个文章时，你应该接触过javascript，甚至熟练运用javascript。javascript是一个伟大的、强大的语言。但是随着web应用变得越来越大，我们发现很难去维护javascript的代码。因此，javascript显得十分困难和消耗时间。

伴随着javascript框架的出现，包括客户端javascript框架和服务端javascript框架，extjs是客户端javascript框架之一。
<!-- more -->
本章节主要是extjs的基本介绍，和使用一些必要的工具，搭建extjs的开发环境。我们将讨论以下话题：
* extjs的优点
* extjs的介绍
* 安装extjs和Sencha Cmd
* 使用Sencha Cmd搭建extjs应用程序
* 应用程序的架构
* 探索Sencha Cmd的命令
* 调试Extjs应用程序
* 开发工具
  
## 为什么使用Extjs
在web应用程序下，使用extjs有以下优点：
  
### 支持跨浏览器
你可能会花上几个小时甚至几天时间去解决跨浏览器的bug，而没有把精力花费到解决你的业务逻辑上。然而，一个好的javascript框架，像extjs，它帮我们解决了这个任务，让我们把精力关注到我们的业务逻辑上。
  
### 富UI组件
extjs包含大量的富UI组件，譬如data grid、tab、panels、tree controls、date picker、charts等，它们会节省你大量的开发时间。
  
### 双向数据绑定
双向数据绑定意思是：当视图的数据改变，你的模型会自动改变。同样的，当你的应用更新了模型，视图的关联数据也会自动的改变。
举个列子，编辑页面。当你加载页面的时候，你需要把模型的数据展示成html，当用户在视图上修改数据时，你需要更新你的模型，但如果你使用了extjs，extjs自动地帮你完成，你将不需要做任何操作。
  
### javascript构建模式
随着越来越多的代码移到客户端，维护客户端javascript代码变得十分困难。由此产生的MVC(Model View Controller)/MVVM(Model View, View Model)架构使得客户端代码易于维护，在生产环境使用增长很快。MVC和MVVM将在后面解释。

### 简化复杂的操作
试想一下编辑一段ajax调用的javascript代码，并确保其在所有的浏览器中运行正确。让我们看一下在其他javascript框架中ajax调用的源码。试想一下在纯javascript中创建一个复杂的控件譬如grid，并包含如分页、排序、过滤、分组、快捷键、可编辑等等功能。

### 简单的dom访问
在纯javasript中，你可以访问dom，但它是那么的复杂。

### 客户端路由
在许多web应用程序中，路由指根据url访问web页面并执行逻辑。路由可以在服务端也可以在客户端。通常，客户端路由是用于单页面应用。

## extjs介绍
extjs几乎是一个一站式的开发富UI应用的框架。它提供MVC、MMVM、双向绑定、跨浏览器兼容、路由、可扩展的富UI组件集合、图表等。extjs还拥有完整的api文档。extjs起源于一个第三方库YUI，它现在是Sencha公司的一个产品。
使用extjs，你将大部分都是写javascript代码，基本上你不用写html代码。extjs装载着大量的富UI组件可以节省你的开发时间。

