title: Castle开发平台手册
date: 2016-04-24 12:35:39
categories: 
- 架构设计
tags: 
- java

---

<h2 id="intro">前言</h2>Castle的目标是打造一个高性能、高扩展性的java开发平台，适合于开发各种互联网软件产品。
<!-- more -->

<div class="github-widget" data-repo="xiangxik/castle"></div>

## 特点
*
* 可以采用单一服务集成，也可选择地使用第三方服务管理框架（例如dubbo）。

## 工程用途说明
* application: 平台包，项目引入该包即可包含了主要功能，依赖于全部关键module包。
* module-base: 构成平台的基础包。
* module-domain: 构成平台的领域数据操作包，依赖于module-base。
* module-cache: 构成平台的缓存功能包，依赖于module-domain。
* module-mongodb: mongodb功能包。
* module-netty: netty功能包。
* module-redis: redis功能包。
* module-web: 构成平台的web功能包，依赖于module-domain。
* module-web-bootstrap: 构成平台的bootstrap包，依赖于module-web。
* module-web-easyui: 构成平台的easyui包，依赖于module-web。
* module-web-extjs: 构成平台的extjs包，依赖于module-web。
* module-security: 构成平台的安全包，依赖于module-web。
* extension-cms: 扩展平台包。包含cms的功能。引入该包即拥有cms功能。
* extension-mall: 扩展平台包。包含商城及支付等功能。引入该包即拥有商城功能。
* extension-wechat: 扩展平台包。包含微信网站的展示和微信相关功能。
* plugin-base: 插件基础包。
* plugin-payment: 支付插件包。