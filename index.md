---
layout: page
title: Mookrs
tagline: Remember.Let go.Move on.
---
> 这里是Mookrs的个人博客，采用[Jekyll](https://github.com/mojombo/jekyll)搭建，托管在[Github](https://github.com)上。
>
> Remember. Let go. Move on. I will miss it more than I can ever say.


<ul class="posts">
{% for post in site.posts %}
<li><span class="index-date-tag-fixed-width">{{ post.date | date_to_string }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>

