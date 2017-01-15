---
title: 'Blog'
---
{% for post in site.posts %}
# [{{ post.title }}]({{ post.url }})

### {{ post.date | date: "%B %-d, %Y - %I:%M %P" }}

{{ post.excerpt }}{% endfor %}
