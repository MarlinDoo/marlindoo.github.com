---
layout: page
title : Angular-UI
header : Post Archive
---
《MEAN Machine》，介绍MEAN框架体系。作者在Angular路由部分用一小段文字介绍了AngularUI，功能很是诱人，文字如下：

虽然ngRoute是为Angular打造的最契合的路由工具，但AngularUI团队推出了另一个路由框架叫做UI Router。作为Angular应用套件来与其协同工作。AngularUI在Angular中，为使用Bootstrap Javascript组件提供了诸如UI Router、UI Bootstrap等许多有用的工具。

UI Router与ngRoute实现方式不同，它基于嵌套的状态而不仅仅基于路由URL来修改应用视图。这意味着应用不需要绑定URL路径，通过应用的状态来调用不同的显示模板（例如用户登录状态）。

UI Router嵌套状态的能力也可以带来很多的好处。ngRoute并没有提供这些功能。 UI Router还提供一些高级的UI功能，这对于有多个侧边栏面板和可移动组件的场景很有帮助。在移动端应用中，有很多这样的应用场景。

Angular UI 介绍[AngularJS Routing Using UI-Router](https://scotch.io/tutorials/angular-routing-using-ui-router)

原文如下：

While ngRoute is the routing tool built to work most closely with Angular, another tool called UI Router was built as another routing framework by the AngularUI team. AngularUI is the companion suite that works hand in hand with Angular applications. They provide many useful tools like UI Router, UI Bootstrap for using Bootstrap JavaScript components within Angular, and a few other awesome tools.

UI Router provides a different approach than ngRoute in that it changes your application views based on state of the application and not just the route URL. This means that your application is not tied to the URL path and you can adjust what templates show based on application state (ie if a user is logged in or not).

There are also great benefits by having the ability to nest states. ngRoute doesn’t provide this functionality and for more advanced UIs, it is helpful to have nested states like having multiple sidebar panels and moving components you would see more in mobile applications.

We will be using ngRoute since it is the standard, but for more reading on UI Router, here’s a good starting article: AngularJS Routing Using UI-Router. In the future, the Angular team has stated that the next routing module they build will have features from both ngRoute and UI Router.