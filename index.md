---
layout: page
title: Mookrs
tagline: fuck
---

ifffffff
fasjfklasjlfsklfjklsajfkla
Here's a sample "posts list".
中文啊
<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>



