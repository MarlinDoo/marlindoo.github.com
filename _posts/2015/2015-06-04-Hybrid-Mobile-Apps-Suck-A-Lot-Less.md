---
layout: page
title : HYBRID MOBILE APPS SUCK A LOT LESS
header : Post Archive
---

# 混合移动应用逐步成熟

原文地址[HYBRID MOBILE APPS SUCK A LOT LESS](http://wiredcraft.com/blog/hybrid-mobile-apps-suck-a-lot-less/)

我们最近在研发一款短途分享移动端应用，这个应用与Twist打交道（当它发布之后会有更多功能迁移到该应用上）。开发日程安排很紧张，同时我们知道，如果使用Objective-C 开发，iOS原型的发布时间将难以确定。

几年前，我们团队使用Backbone.js和Phonegap技术为联合国开发了一款内部移动应用，结果并不理想：调试过程很痛苦，优化非常困难，用户体验与原生应用相比槽糕太多。

尽管如此，我们决定重新评估混合型应用；我们团队有很多优秀的JS开发工程师，他们实践着这种开发方式，我们可以非常非常快的发布一款简单应用。

# 工具

我们选择AngularJS搭配React，作为前端应用框架。下面是我们正在使用的工具集：

* [Ionic](http://ionicframework.com/)：由AngularJS和Cordova组成的前端框架。强烈推荐大家玩玩。它不仅仅看起来漂亮。
* [Ng-cordova](http://ngcordova.com/)：构建并发布应用工具，他在Cordova API的上层提供了一些AngularJS扩展。
* [Crashlytics](http://try.crashlytics.com/)：用于发布Beta版本（App Store的审批需要一段时间）并能提供报告缺陷方案。
* [Gulp.js](http://gulpjs.com/) 和 [Ionic CLI](https://github.com/driftyco/ionic-cli)用于自动化构建工具，用于自动化我们大部分的构建工作。
* [Chrome Dev Tool](https://developer.chrome.com/devtools)是一款非常棒的调试、优化工具，基本覆盖了我们绝大部分需求。
* 我们使用Coffeescript开发，使用Jade模板和SASS(CSS预处理器)生成HTML和CSS。

# 经验

* 不好的经验：
    - 你依然需要在真机上做大量的测试工作，开发没有变得那么轻松；
    - 你依然需要Objective-C和Xcode的只是，尤其是处理依赖和性能问题的时候。
    - 某些事情依旧坎坷，比如处理键盘就非常纠结。
    - 某些UI组件，比如地图，需要大量的优化工作。
* 好经验：
    - 你可以使用开发Wep App时使用的所有工具，包括在浏览器中进行调试。所需工具集可共用。
    - 使用原生插件像调用Web API一样轻松。
    - Ionic有一个非常好的社区。
    - 当使用混合开发方式，你可以进展很快，彻底缩短实现原型的时间。

# 什么时候采用混合开发？

如果有足够的资源和时间，我们当然倾向使用原生方式实现；混合应用有其优化的天花板。如果你满足下面几点，我建议可以使用 Cordova + AngularJS + Ionic 方案：

* 你想快速得到一个原型；
* 你的应用依赖大量的通讯（调用在线 API)；
* 在应用内部需要处理大量计算；
* 没有太多动态视图；
* 访问硬件设备API；
* 你不熟悉Objective-C/Xcode 或 Android/Java。

==================
# 原文

We recently worked on a ride sharing mobile app with an interesting twist (more on that when it is released). Deadlines were tight and, while we know our way around Objective-C, we weren’t sure we could deliver a first working iOS prototype in time.

A few years back, our team built an internal mobile application for the UN using Backbone.js and Phonegap, and the experience had been less than ideal: debugging was a pain, optimization was excruciatingly hard and the overall UX was way worse than native.

Nonetheless, we decided to re-evaluate hybrid apps; we have a fair amount of JS developers on the team and using this approach, we could whip out a simple app fairly quickly.

The tools

We wanted to use AngularJS as it is, with React, our JS framework of choice for front-end apps. Here’s what we effectively used:

Ionic; a front-end framework combined with AngularJS and Cordova. I highly recommend you check out. It offers way more than eye candy.

Ng-cordova: will help you build and deploy your apps, it provides some AngularJS extensions on top of the Cordova API.
Crashlytics: for beta releases (the App Store approval process takes a while) and bug reporting solution.

Gulp.js and the Ionic CLI to automate most of our builds.
The Chrome Dev Tool is awesome enough to cover most of needs for debugging and optimization.
We wrote in Coffeescript and used Jade and SASS for generating the HTML and CSS.
Our experience

The bad:
You still need to do a lot testing on actual devices, don’t expect things to always work out-of-the-box,
You still need some knowledge of Objective-C and Xcode, particularly when dealing with dependencies and performance issues.
Some things are still pretty buggy; dealing with keyboards for example is pretty wacky.

Some UI components like maps may require a good deal of performance tuning.

The good:
You can use anything you would developing a Web app, including testing in the browser. The tool-belt required
Using native plugins is as easy a querying a Web API.
Ionic has a great community.
You can move extremely fast, the time to prototype was radically shorter
When to go hybrid
Given more resources and time, we would likely still go for native; there’s a limit to the level of polish you can reach with a hybrid app. With that being said, if you check on enough of the following points, I’d consider give the Cordova + AngularJS + Ionic setup a go:

You want to get a prototype out fast,
Your app relies a lot on connectivity (use of online APIs),

You have no heavy duty processing to do in-app,
You don’t have overly dynamic views,
Access call hardware api,
You’re not that familiar with Objective-C/Xcode or Android/Java.
