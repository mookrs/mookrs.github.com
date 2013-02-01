---
layout: page
---

I am a student of WHU. On the internet I usually use the ID "Mookrs". The website is still under building, just have your fun! :)

### Recent posts
<ul class="posts">
{% for post in site.posts limit:10 %}
<li><span class="index-date-tag-fixed-width">{{ post.date | date_to_string }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>