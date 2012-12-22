---
layout: page
title: 蘑殼四研究所
tagline: 
---
{% include JB/setup %}

> Remember. Let go. Move on. I will miss it more than I can ever say.

#### Recent posts
<ul class="posts">
{% for post in site.posts limit:10 %}
<li><span class="index-date-tag-fixed-width">{{ post.date | date_to_string }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>