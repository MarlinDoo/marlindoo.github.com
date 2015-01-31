---
layout: page
title : Marionette中Layout与region有什么区别？
header : Post Archive
---

本文是 Marionette 作者 Derick Bailey 在Stackoverflow上对该问题做的回答。

## 问题：
Marionette provides two components named Regions and Layouts. At first glance, they seem to provide similar functionality: A location on the page for my application to place subviews, plus some additional event binding fairy dust.

Marionette 提供了Regions和Layouts两种组件，二者在功能上很相似：在应用页面上的一块地方，用于加载子视图，并提供一些事件的绑定。

Looking under the hood, it's fairly clear that each component is implemented in a very different way, but I'm not sure why and when I would want to use one over the other. What use cases are each component intended for?

再仔细探究，这两个组件实现方式有很大区别。我想了解，在什么情况下，出于什么样的原因来决定使用Region或Layout。

## 答：

Layouts and Regions serve very different purposes: a layout is a type of view, but a region will display a view in your HTML/DOM for you. A region may be used to display a layout. And a layout will also contain regions. This creates a nested hierarchy that can extend infinitely.

Layouts 和 Regions 有着各自不同的用途：layout是一类视图，而region被用于在HTML/DOM中显示视图。Region可用来显示一个layout。Layout可以包含一个或多个regions。这将创建一个嵌套的分层结构，并可以无限延伸。

### Region

A Region manages the content that is displayed within an HTML element on your web page. This is often a div or other "container" like element. You provide a jquery selector for the region to manage, and then you tell the region to show various Backbone views in that region.

Region管理着Web页面上一块由HTML元素限定的内容区域。Html元素常常使用div或者其他类“容器”标签。我们可以为Region管理提供一个jquery选择器，在region中显示各种Backbone视图。

{% highlight javascript linenos %}

<div id="mycontent"></div>

MyRegion = new Backbone.Marionette.Region({
  el: "#mycontent"
});

myView = new MyView();
myRegion.show(myView);

{% endhighlight %}

A region, then, is not directly rendered and does not have it's own DOM interactions or updating. It is purely for the purpose of displaying a view at a specified point in the DOM, allowing different views to be swapped in and out, easily.

Region，并不直接渲染视图，也没有自己的DOM交互或更新。其目的很单纯，在DOM树上的指定节点显示一个视图，并控制不同的视图在该节点加载和删除。

You can read more about Regions, here: http://lostechies.com/derickbailey/2011/12/12/composite-js-apps-regions-and-region-managers/

获取更多关于Region的信息 [http://lostechies.com/derickbailey/2011/12/12/composite-js-apps-regions-and-region-managers/](http://lostechies.com/derickbailey/2011/12/12/composite-js-apps-regions-and-region-managers/)

## Layout

A Layout is a specialized type of view. It extends from Marionette.ItemView directly, which means it is intended to render a single template and may or may not have a model (or "item") associated with that template.

Layout 是一类特殊类型的视图，由Marionette.ItemView 直接扩展而来，它可用于渲染单一模板，这个模板可以关联model，也可以不关联model。

The difference between a Layout and an ItemView is that a Layout contains Regions. When you define a Layout, you give it a template but you also specify regions that the template contains. After rendering the layout, you can display other views within the layout using the regions that were defined.

Layout和ItemView的不同之处在于Layout包含Region。当我们定义了一个Layout，我们提供给Layout模板的同时可以指定模板中包含的Region。当Layout渲染完毕，我们可通过在Layout中预先定义的Region来显示其他视图。

{% highlight javascript linenos %}

<script id="my-layout" type="text/html">
  <h2>Hello!</h2>
  <div id="menu"></div>
  <div id="content"></div>
</script>

MyLayout = Backbone.Marionette.Layout.extend({
  template: "#my-layout",

  regions: {
    menu: "#menu",
    content: "#content"
  }
});

layout = new MyLayout();
layout.render();

layout.menu.show(new MyMenuView());
layout.content.show(new MyContentView());

{% endhighlight %}

## Regions And Layouts Together

You can already see that Layouts and Regions are related, though they provide separate functionality. But a Layout and a Region can be used together to create sub-layouts and nested hierarchies of layouts, regions and views.

我们已经了解了Layouts和Regions之间的关系，以及二者功能侧重点。Layout和Region可以一起用于创建sub-layout和嵌入层级关系的Layouts，Regions和视图。

{% highlight javascript linenos %}

<script id="my-layout" type="text/html">
  <h2>Hello!</h2>
  <div id="menu"></div>
  <div id="content"></div>
</script>

<div id="container"></div>


container = new Backbone.Marionette.Region({
  el: "#container"
});

MyLayout = Backbone.Marionette.Layout.extend({
  template: "#my-layout",

  regions: {
    menu: "#menu",
    content: "#content"
  }
});

// Show the "layout" in the "container" region
layout = new MyLayout();
container.show(layout);

// and show the views in the layout
layout.menu.show(new MyMenuView());
layout.content.show(new MyContentView());

{% endhighlight %}

You can nest any number of layouts and regions together, with any number of views, using any view type that extends from Backbone.View (not just Marionette views).

我们可以扩展Backbone.View(并不只是Marionette Views)来生成任何类型的视图，并将这些视图嵌入任意数量的Layouts和Regions。

原文地址 [What the difference between a marionette layout and a region](http://stackoverflow.com/questions/10521266/whats-the-difference-between-a-marionette-layout-and-a-region)
