---
layout: page
title: MarlinDoo
tagline: Making Joywok since 2009.
---
{% include JB/setup %}

## Profiles 

github: [http://github.com/MarlinDoo](http://github.com/MarlinDoo)!

stackoverflow: [http://stackoverflow.com/users/1890869/marlin](http://stackoverflow.com/users/1890869/marlin)

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




