---
title: Blog
---
# Latest
{% for post in site.posts limit:10 %}
## [{{ post.title }}]({{ post.url }})
{% endfor %}
# Categories
{% for category in site.categories %}
## [{{ category[0] }}](/blog/categories#{{category[0]}})
{% endfor %}
