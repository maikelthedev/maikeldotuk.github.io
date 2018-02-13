---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
---
{% for post in site.posts %}
<div style="float:right; margin-top: 10px;">
  <small>{{ post.date | date: '%A, %-d %B %Y' }}</small></div>
  <h2><a style="text-decoration:none;" href="{{ post.url }}">> {{ post.title }}</a></h2>
  <div onclick="window.location='{{ post.url }}';" style="cursor: pointer; text-decoration:none; color: white" >{{ post.excerpt }}</div>
{% endfor %}
---
