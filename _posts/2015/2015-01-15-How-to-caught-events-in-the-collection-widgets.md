---
layout: page
title : How to caught events in the collection widgets？
header : Post Archive
---

在Marionette体系中，Modules之间事件传递，由Application作为中间人（mediator），进行事件的传递。
当页面上存在相同的一组widgets时，各个widget如何准确捕获与自己相关的事件？
典型的场景如信息流评论，页面上有多条信息流，每条信息流都有自己的评论发布栏和评论列表，点击某条评论的“回复”按钮时，其对应的评论发布栏widget捕获该事件。其他的评论发布栏则不关心该事件。
实现方案如下：

在评论列表 Widget 为每条评论的“回复”按钮添加事件
{% highlight javascript linenos %}

MyApp.vent.trigger('reply:comment:'+postId, platform);

{% endhighlight %}


在评论发布栏 Widget中
{% highlight javascript linenos %}

this.listenTo(MyApp.vent, 'reply:comment:'+this.model.get('id'), function(platform) {
  // ...
});

{% endhighlight %}