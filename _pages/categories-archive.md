---
title: "Posts by Category"
layout: categories
permalink: /categories/
author_profile: true
---

{% for post in site.categories.Personal %}
 <li><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}