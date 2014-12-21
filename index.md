---
layout: page
title: MarlinDoo
tagline: Makeing Joywok since 2009.
---
{% include JB/setup %}


## 热浪岛日出
![热浪岛日出]({{ site.url }}/assets/images/Redang.jpg)

## Sample Posts

This blog contains sample posts which help stage pages and blog data.
When you don't need the samples anymore just delete the `_posts/core-samples` folder.

    $ rm -rf _posts/core-samples

Here's a sample "posts list".

## site.time: {{ site.time }}
## site.pages

从下面的截图可以看到：
![有帮助的截图]({{ site.url }}/assets/images/yeoman_logo.jpeg)

{% highlight ruby linenos %}
def show
  @widget = Widget(params[:id])
  respond_to do |format|
    format.html # show.html.erb
    format.json { render json: @widget }
  end
end
{% endhighlight %}

<ul class="posts">
  {% for post in site.posts %}
    <!-- <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a><p>{{ post.excerpt }}</p></li> -->
    <li>
      <!-- Here's the header -->
      <header>
        <h2 class="title"><a href="{{ post.url }}">{{ post.title }}</a></h2>
      </header>
      <!-- Your post's summary goes here -->
      <article>{{ post.excerpt }}</article>
    </li>
  {% endfor %}
</ul>

## Profiles 

github: [http://github.com/MarlinDoo](http://github.com/MarlinDoo)!

stackoverflow: [http://stackoverflow.com/users/1890869/marlin](http://stackoverflow.com/users/1890869/marlin)


