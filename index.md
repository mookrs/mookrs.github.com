---
layout: page
title: Mookrs
tagline: fuck
---
需要中文啊少年


Here's a sample "posts list".jiasjfasjfa
dfsjfsjkafja
dffafjijlajf
<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>



