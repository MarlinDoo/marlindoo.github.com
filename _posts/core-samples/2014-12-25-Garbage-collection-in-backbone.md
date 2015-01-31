---
layout: page
title : Garbage collection in Backbone
header : Post Archive
---

Javascript doesn't have any manual memory management, and objects you create can't be garbage collected until they are no longer referenced.

In Backbone.Collection, It'll remove all reference to the model when clear the collection.

## The Code like this

{% highlight javascript linenos %}
reset: function(models, options) {
  options || (options = {});
  for (var i = 0, l = this.models.length; i < l; i++) {
    this._removeReference(this.models[i], options);
  }
  // ... ...
  return models;
},
// Internal method to sever a model's ties to a collection.
_removeReference: function(model, options) {
  if (this === model.collection) delete model.collection;
  model.off('all', this._onModelEvent, this);
}
{% endhighlight %}