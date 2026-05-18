---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
title: Home
hide_title: true
---

## Welcome to *judz.net*
- Learn some more [about]({% link about.markdown %}) me, view my [resume]({{ site.baseurl }}/files/Salinas_Judson_Resume.pdf),
 explore my [projects]({% link projects/index.markdown %}), or check out my [blog]({% link blog/index.markdown %}). 

## Recent Blog Posts
{% for post in site.posts limit:3 %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}

## Recent Projects
{% assign sorted_projects = site.projects | sort: 'year' | reverse %}
{% for project in sorted_projects limit:3 %}
- [{{ project.title }}]({{ project.url }})
{% endfor %}

## Contact Me
- Feel free to [contact me](mailto:judz1105@gmail.com) if you have any quesitons or would like to collaborate.
