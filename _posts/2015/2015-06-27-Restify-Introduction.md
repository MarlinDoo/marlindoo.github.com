---
layout: page
title : restify Introduction
header : Post Archive
---

移动端的发展使得后台技术体系也进入了一个颠覆期。

记得12年接触Node.JS的第一个框架就是Express，对其后台模板Jade也做了一些功课。其框架思路、技术体系都包含有当时的新思想。（当时很有相见恨晚的赶脚。）

当时后台服务的主要目标是浏览器，因此Express体系为浏览器应用提供了大量功能，如模板、渲染等等。不到3年，这项技术已然进入暮年。

现在，后台服务的目标变了，需要为各种客户端提供服务，后台技术体系重点随之转换到API Services的架设上。

Github上，基于Node的方案有很多，如restangular、#node-restify# 等。node-restify 框架简洁，已有3k5 stars。源码值得读一读。

下面的介绍翻译自[Node-Restify](http://mcavage.me/node-restify/)

restify 是一个专门用于创建REST Web服务的node.js模块。由于同样是基于node.js来实现Web应用，它大量借鉴了Express框架。

#为什么选择restify而不是express？

人们最关心的就是这一点，我想脱离开前端来说说。

Express 的应用目标是浏览器应用，它包含了大量的模板、渲染等功能用于支撑这个目标。Restify目标不是这样。

Restify用于创建更“严格”的API服务，这些服务是可维护并可观测的。如果运行的平台支持动态追踪(DTrace)，Restify可以对所有处理程序自动动态追踪。

简单的说，实现restify是因为我需要一个基于HTTP协议并且我能够拥有绝对控制权的平台，基于这个平台的应用可以观测到延迟和特性。如果你不需要这些或者不在乎这些方面，那么他也许不适合你。

加入irc.freenode.net上的 #restify IRC频道可以实时聊天、讨论，并获得支持，



















