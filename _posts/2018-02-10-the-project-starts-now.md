---
title: The Project starts now
layout: posts
date: 2018-02-10 00:00:00 +0000
categories:
- theproject
---
I have started now the Open University end-of-degree project, I can't carry on postponing it until I find a job and now is the weekend so I'm free to study.

This is the first post about the project, they all will have the tag "theproject" so I can filter them quickly.

Today what I've done is to read all the details of TMA01 and started it. I thought it would take me the entire weekend because it is 3000 words. But it didn't **I finished it in the space of 6 hours**. Let's say 7 if we count the time of reading, higlighting and having a rough idea of what was required before I started typing non-stop.

I've never done a TMA this quick. Beware that it is a draft though, not a fully finished one. My tutor wanted an early draft to see how am I going. Hence why I wrote this early. That TMA (which means "tutor-marked assigment") is not due until the 6th of March.

Now, the next step is to start researching elastic clouds. My entire site is in an EC2 in AWS. But I've never made them autoscale.

![](/uploads/2018/02/10/zoho projects.JPG "A gantt chart of my project")

This is a gantt chart of my project outline. It's amazing to think that in 214 days I'll be free of university.

Next post will be about how my research is going.

I've started by adding a "Categories" page as you see above by creating a page with this code.
{% raw %}
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
{% endraw %}
Now I am going to carry on with TMA02 of TM354 (a software development module) and tomorrow back to the project.