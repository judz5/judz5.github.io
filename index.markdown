---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
title: Home
---

## Welcome to *judz.net*
- Learn some more [about]({% link about.markdown %}) me, or check out my [blog]({% link blog/index.markdown %})

## Recent Blog Posts
{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}

## Contact Me
- Feel free to [contact me](mailto:judz1105@gmail.com) if you have any quesitons or would like to collaborate.

