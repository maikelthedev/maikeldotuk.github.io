---
title: Categories
layout: page
date: 2018-02-10 00:00:00 +0000
categories: []
---

<div id="archives">
{% for category in site.categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="#{{ category_name | slugize }}"></div>
    <p></p>

    <h3 class="category-head">{{ category_name }}</h3>
    <a name="{{ category_name | slugize }}"></a>
    {% for post in site.categories[category_name] %}
    <article class="archive-item">
      <h4><li style="list-style-type:square"><a style="text-decoration: none" href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a> <small>{{ post.date | date: '%A, %-d %B %Y' }}</small></li></h4>
    </article>
    {% endfor %}
  </div>
{% endfor %}
</div>
