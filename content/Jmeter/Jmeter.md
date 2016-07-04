---
title: "Jmeter"
layout: page
date: 2016-05-27 00:00
---

[TOC]

# 跳过sso #
----
目前仅是美团sso登录使用方法，点评sso登录不可用(需之后了解sso逻辑)

1.保存cookie，使用firefox的firebug工具

![cookie](/attach/cookie.jpg)

2.将cookie导入jmeter的“http cookie 管理器”中

![jmeter](/attach/jmetercookie.jpg)

3.发起http请求


# Java接口测试 #
------
* 编写Java脚本，详细请查看：[java脚本](/Java/Jar.html)

* 将Jar包放入jmeter路径下
	/lib/ext

* 添加Java请求，自动加载jar包中的类，输入参数即可

![javajmeter](/attach/javajmeter.jpg)
