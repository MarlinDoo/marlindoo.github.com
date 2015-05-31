---
layout: page
title : Whats-the-best-UI-framework-of-Onsen-UI-or-Ionic
header : Post Archive
---

最近准备做一个Cordova项目，准备为应用挑选一款移动Web应用UI框架。由于前端一定要使用MV*框架，因此把jQueryMobile直接排除，Github上排名靠前的明星框架就剩下Ionic和OnsenUI，于是找了一些二者比较的文章。
下面这篇文章翻译自 [http://www.quora.com/Whats-the-best-UI-framework-of-Onsen-UI-or-Ionic](http://www.quora.com/Whats-the-best-UI-framework-of-Onsen-UI-or-Ionic)，作者 [Dragan Gaić](http://www.quora.com/Dragan-Gai%C4%87)。文中对Ionic和OnsenUI客观的比较，使读者能快速对二者的特点有一个了解，并根据项目的需求来确定目标框架。

What's the best UI framework of Onsen UI or Ionic?

OnsenUI和Ionic中，谁是最好的UI框架？

One year has passed since both frameworks are available on the market. Onsen UI is currently in stable 1.2 version while Ionic is in the last release candidate state.

两个框架诞生至今已经有一年了，OnsenUI目前发布了1.2稳定版，Ionic处于最新发布的候选状态。
[译者注]2015-03-05 Ionic发布了1.0.0-rc.0版本。

I have worked with both of them so let me give you a short overview, I also wrote a much larger blog article, you'll find it at the end of this answer.

因为在实际项目中使用过这两个框架，所以让我来简单的介绍一下。本文最后附上我曾写过的一些关于二者其他的文章。

I won't go into much details about the core framework; if you have a previous AngularJS knowledge you will easily transition to Ionic or Onsen UI.

我不会深入介绍框架核心；如果你以前有AngularJS的经验，你很容易过渡到Ionic货OnsenUI。

* Both frameworks are built around AngularJS and they heavily depend on directives, you can also easily build your own custom directives. Onsen UI also features a jQuery support (unnecessary if you ask me).
* 两个框架都是基于AngularJS构建，并且都非常依赖指令集，你也可以轻松的构建你自定义的指令（？）。Onsen UI还有一个特性，支持jQuery（如果你问我的话，这个没有必要）。
* Both frameworks support Android 4+, iOS 6+ (some features are available on Android 2.3), Onsen UI also officially supports Firefox OS and desktop browsers. Ionic don't have an official desktop support, but it will still work (it will not be pretty, imagine ).
* 两个框架同时支持 Android 4+，iOS 6+ （一些特性在Android 2.3上有效），Onsen UI官方支持Firefox操作系统和桌面浏览器。 Ionic 没有提供桌面端的官方支持，不过还是可以运行（可以想象，运行的不会太好）。
* Ionic currently don't support Windows Mobile platform (it will have it in the future), Onsen UI support is currently in development (since November 2014).
* Ionic目前不支持Windows移动平台（将来某一天会支持），Onsen UI正在开发对该平台的支持（从2014年11月开始）。
* Both frameworks support some kind of splitview feature so they can be used for table development.
* 两个框架都支持一些分屏特性，因此，他们都可以用于表（？）的开发。
* Both frameworks have a distinctive nice looking flat UI. I prefer Ionic over Onsen UI look and feel, but this is a matter of personal taste. Both default themes look iOS 7 like.
* 两个框架都有各自独特漂亮的扁平化UI。我个人更喜欢Ionic的外观和体验，不过这一点因人而异。二者默认的主题很像iOS7风格。
* Onsen UI supports native looking themes for Android and iOS. Ionic framework uses the same theme for all platforms, but some features will depend on the platform (for example tab look and feel)
* Onsen UI支持Android和iOS的原生外观风格。Ionic框架对所有平台使用一直的风格，但某些特性依赖于平台支持（例如Tab的外观和体验）。
* Both frameworks have a working theme builder.
* 两个框架都有主题生成器。
* Ionic supports SASS while Onsen UI is built around Topcoat CSS library.
* Ionic支持SASS，Onsen UI基于Topcoat CSS库构建。
* Both frameworks have a large widget support (directives)
* 两个框架都有一个大组件支持（指令）（？）
* Onsen UI has a better documentation. It is separated at two different locations. First one is “Components” where you can see different directives and each one has a working example you can use and replicate. Second part is a “Guide” where you are guided through the application creation process.
* Onsen UI 的文档更好，该文档分为两个不同的位置。第一个是你可以找到的不同指令组件，每一个都拥有可运行的例子，可以直接复制和使用。第二部分是“指南”，可以指导你的开发过程。（？）
* Ionic has a disorganized documentation (heavily fragmented). It lacks a real “getting started” tutorial, even if you have previous AngularJS experience. It shows you pieces, but not how to connect them correctly.
* Ionic的文档很混乱。即使以前有AngularJS经验，对于你，依旧缺少一个真正的“入门”教程。这些文档支离破碎，难以搞清如何把他们正确的串联起来。
* On the other hand Ionic has much larger community so you will easily find problem solutions.
* 另一方面，Ionic有更大的社区，方便开发人员轻松的获得问题答案。
* Ionic framework has a great official forum + large StackOverflow community. At the same time, Onsen UI uses only StackOverflow as a help center (I would call this a fail).
* Ionic框架有强大的官方论坛+更大的StackOverflow社区。Onsen UI仅仅使用StackOverflow作为帮助中心（我不得不说这是一个败笔）。
* Onsen UI has an HTML5 IDE called MONACA IDE (great tool), Ionic IDE is currently in production, you can participate in beta test.
* Onsen UI提供了HTML5 IDE，命名为MONACA IDE（好工具），Ionic IDE还在开发中，你可以参与它的Beta测试。
* Ionic has a growing 3rd party plugin community (for example date picker), I couldn't find any 3rd party Onsen UI plugin
* Ionic有越来越多的第三方插件社区（例如Date Picker），目前还没有发现Onsen UI插件社区。

I wrote a much larger article covering Ionic / Onsen UI changes, find it [here](http://www.gajotres.net/ionic-vs-onsenui/).
我写了一篇包含了Ionic / Onsen UI变化的更详细的文章，[文章链接](http://www.gajotres.net/ionic-vs-onsenui)。
